---
layout: post
title: "Masked batchnorm in PyTorch"
date: 2020-03-16 00:00:00 -0800
---

If you just want to see the code, it's in a [gist](https://gist.github.com/yangkky/364413426ec798589463a3a88be24219). 

## Introduction: Sequence tokenization and padding

Sometimes the fact that all proteins are not the same length is the bane of my existence. 

One way we deal with variable-length sequences in machine learning is to pad them all to the same length. For example, if I have the following nucleotide sequences:

```
AGCTAG
AGCTAGA
AGCTA
```

I can right-pad them by introducing a special padding token, let's call it `p`.

```
AGCTAGp
AGCTAGA
AGCTApp
```

And then I can use this as a batch input to the machine-learning model of my choice by assigning each nucleotide and the padding token an integer:

```
x = torch.tensor(
    [
		[0, 2, 1, 3, 0, 2, 4],
		[0, 2, 1, 3, 0, 2, 0],
		[0, 2, 1, 3, 0, 4, 4]
    ]
)
```


If I want to put sequences through a transformer or RNN or CNN and I don't want the model to be affected by the padding, I can also pass in a mask (`mask = (x != 4)`) and use that mask to set things to zero where appropriate. For example, the PyTorch [`Transformer`](https://pytorch.org/docs/stable/nn.html#transformer) class uses this sort of mask (but with a `ByteTensor`) for its [`src`/`tgt`/`mask`]`_padding_mask` arguments. 

## Trying to extend PyTorch's [batchnorm](https://arxiv.org/abs/1502.03167)

Unfortunately, [`nn.BatchNorm1d`](https://pytorch.org/docs/stable/nn.html#torch.nn.BatchNorm1d) doesn't support this type of masking, so if I zero out padding locations, then my minibatch statistics get artificially lowered by the extra zeros. Given Pytorch's object-oriented nature, the most elegant way to implement masked batchnorm would be to extend one of their classes and modify the way minibatch statistics are calculated. 

Starting at [`nn.BatchNorm1d`](https://pytorch.org/docs/stable/_modules/torch/nn/modules/batchnorm.html#BatchNorm1d), we find that all this class implements is a method for checking input dimensions: 

```
    def _check_input_dim(self, input):
        if input.dim() != 2 and input.dim() != 3:
            raise ValueError('expected 2D or 3D input (got {}D input)'
                             .format(input.dim()))
```

It's superclass ([nn._BatchNorm](https://github.com/pytorch/pytorch/blob/master/torch/nn/modules/batchnorm.py#L76)) has a `forward` method, which checks whether to use `train` or `eval` mode, retrieves the parameters needed to calculate the moving averages, and then calls [`F.batch_norm`](https://github.com/pytorch/pytorch/blob/8bae1ed14489f1fbdd1272807779e7a615fda020/torch/nn/functional.py#L1887). `F.batch_norm` in turn calls `torch.batch_norm`. Clicking on that in github leads back to `F.batch_norm`: I think it must be actually implemented in the lower-level cpp code. 

In any case, it looks like there's no straight-forward way to extend PyTorch's batchnorm implementation, so time to write it from scratch. 

## MaskedBatchNorm1d

Given a `(B, 1, L)` mask, we first mask and then compute the number of unmasked locations over which to calculate the minibatch statistics: 

```
if input_mask is not None:
    masked = input * input_mask
    n = input_mask.sum()
```
Then calculate the minibatch mean:

```
masked_sum = masked.sum(dim=0, keepdim=True).sum(dim=2, keepdim=True)
current_mean = masked_sum / n

```

And the minibatch variance: 

```
current_var = ((masked - current_mean) ** 2)
current_var = current_var.sum(dim=0, keepdim=True).sum(dim=2, keepdim=True) / n

```

The full module is available as a [gist](https://gist.github.com/yangkky/364413426ec798589463a3a88be24219). 

## Limitations

Because I didn't want to dig deeper into PyTorch source, there's a few limitations here. 

1. It's almost certainly not as fast as the native PyTorch implementation. 
2. If you're doing [multi-GPU training](https://yangkky.github.io/2019/07/08/distributed-pytorch-tutorial.html), minibatch statistics won't be synced across devices as they would be with Apex's [SyncBatchNorm](https://github.com/NVIDIA/apex/blob/master/apex/parallel/sync_batchnorm.py). 
3. If you're doing mixed-precision training with [Apex](https://nvidia.github.io/apex/amp.html), you can't use level `O2` because it won't detect that this is a batchnorm layer and keep it in float precision. 


