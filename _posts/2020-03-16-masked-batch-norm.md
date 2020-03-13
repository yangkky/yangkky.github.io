---
layout: post
title: "Masked batch norm in PyTorch"
date: 2020-03-13 00:00:00 -0800
---

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


