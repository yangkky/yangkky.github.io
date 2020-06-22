---
layout: post
title: "Two approaches to faster attention"
date: 2020-06-22 00:00:00 -0800
---

Two recent papers introduce approximations to [Transformer](https://arxiv.org/abs/1706.03762) self-attention with runtime $\ll L^2$. 

1. [Masked Language Modeling for Proteins via Linearly Scalable Long-Context Transformers
](https://arxiv.org/abs/2006.03555) introduces *Fast attention via orthogonal random features* (FAVOR). 
2. [Linformer: Self-Attention with Linear Complexity](https://arxiv.org/abs/2006.04768) introduces *linear self-attention*. 

I'm going to summarize the main contribution of each paper, but you should definitely go read them for details such as theorems and theoretical insights. I also write everything using the notation from the FAVOR paper for consistency. 

## Transformer dot-product attention

Let $L$ be the size of an input sequence of tokens. Then transformer dot-product attention is a mapping which accepts matrices $\mathbf{Q}$, $\mathbf{K}$, $\mathbf{V} \in \mathbb{R}^{L×d}$ as input where $d$ is the hidden dimension. Matrices $\mathbf{Q}$, $\mathbf{K}$, and $\mathbf{V}$ are intermediate representations of the input and their rows can be interpreted as queries, keys and values of the continuous dictionary data structure respectively. Transformer dot-product attention is defined as

$$
\operatorname{Att}(\mathbf{Q}, \mathbf{K}, \mathbf{V}) = \mathbf{D}^{-1}\mathbf{AV}
$$

where the attention matrix is $\mathbf{A} = \operatorname{exp}\left(\frac{\mathbf{QK^T}}{\sqrt{d}}\right)$ and $\mathbf{D} = \operatorname{diag}(\mathbf{A1_L})$ is the normalizing factor. For details, see the original paper or this [post](https://nlp.seas.harvard.edu/2018/04/03/attention.html) from Harvard NLP. 

While dot-product attention has proven very useful, its runtime and memory scale as $O(L^2d + Ld)$ and $O(L^2)$, respectively, because $\mathbf{A}\in \mathbb{R}^{L\times L}$ must be computed and stored explicitly. In practice, applications in natural language processing commonly limit the sequence length to 512 or 1024. This is also a significant constraint when modeling proteins. For example, *Streptococcus pyogenes* CRISPR-Cas9 is 1368 amino acids long. 

## Fast attention via orthogonal random features (FAVOR)

The attention matrix $\mathbf{A}$ can be decomposed as 
$$\mathbf{A} = \mathbf{D_Q B D_K}$$
with 

$$
\mathbf{D_T} = \operatorname{diag}\left[  \operatorname{exp}\left(\frac{\|\mathbf{T}_1\|_2^2}{2\sqrt{d}}\right)\ldots  \operatorname{exp}\left(\frac{\|\mathbf{T}_L\|_2^2}{2\sqrt{d}}\right)\right]
\forall \: \mathbf{T} \in \{\mathbf{Q}, \mathbf{K}\}
$$

and 

$$
\mathbf{B} \in \mathbb{R}^{L \times L}, B_{i, j} = \operatorname{exp}\left(-\frac{\|\mathbf{Q}_i - \mathbf{K}_j\|}{2\sqrt{d}}\right)
$$

Naively, $\mathbf{D_T}$ requires $O(Ld)$ time to compute while $\mathbf{B}$ requires $O(L^2d)$, arriving at the overall time complexity of $O(L^2d + Ld)$ for dot-product attention. 

FAVOR is a fast method for approximating $\mathbf{B}$. $\mathbf{B}$ is a the Gaussian (squared-exponential) kernel matrix between the rows of $\mathbf{Q}$ and $\mathbf{K}$ with $\sigma = d ^ {\frac{1}{4}}$. Like most kernels used in machine learning, the Gaussian kernel has a fast random feature approximation. Given a random mapping $\phi: \mathbb{R}^d \to \mathbb{R}^M$ of the form 

$$
\phi(\mathbf{x}) = \sqrt{\frac{2}{M}}\operatorname{cos}(\mathbf{Wx} + \mathbf{b})^T
$$

where $W_{i, j} \sim \mathcal{N}(0, \sigma^2)$ and $b_i ~\sim \operatorname{Unif}(0, 2\pi)$. As described in the paper, choosing orthogonal random features instead of sampling independently decreases the variance of the approximation. 


$$
K(\mathbf{x}, \mathbf{y}) = \mathbb{E}\left[\phi(\mathbf{x})^T\phi(\mathbf{y})\right]
$$

Define randomly-featurized keys and queries as $\mathbf{\hat{Q}} = \sqrt{\frac{2}{M}}\operatorname{cos}(\mathbf{WQ}^T + \mathbf{b})^T$ and $\mathbf{\hat{K}} = \sqrt{\frac{2}{M}}\operatorname{cos}(\mathbf{WK}^T + \mathbf{b})^T$. Combine these with $\mathbf{D_T}$: $\mathbf{Q'} = \mathbf{D_Q}\mathbf{\hat{Q}}$ and $\mathbf{K'} = \mathbf{D_K}\mathbf{\hat{K}}$. Therefore,
$$
\mathbf{A} = \mathbb{E}\left[\mathbf{Q'}\mathbf{K'}^T\right]
$$

And $\mathbf{\hat{A}} = \mathbf{Q'}\mathbf{K'}^T$ is an unbiased estimator of $\mathbf{A}$. However, would still like to avoid computing and storing the full $L \times L$ attention matrix. We can do this when calculating approximate dot-product attention by being clever in how we group the matrix multiplications:

$$
\operatorname{\hat{Att}}(\mathbf{Q}, \mathbf{K}, \mathbf{V}) = \mathbf{\hat{D}}^{-1}\mathbf{\hat{A}V}
 = \mathbf{\hat{D}}^{-1}(\mathbf{Q'}(\mathbf{K'}^T\mathbf{V}))
$$

with 

$$
\mathbf{\hat{D}}^{-1} = \operatorname{diag}(\mathbf{Q'}(\mathbf{K'}^T\mathbf{1}_L))
$$

This requires $O(LMd)$ time and $O(Md + Ld + ML)$ space. 


<!--Estimate of $B$ is unbiased -- estimate of $A$ is not
-->
<!--introduces a notion of generalized attention, where the attention matrix $\mathbf{A}$ is decomposed into $\mathbf{A} = \mathbf{D_Q B D_K}$, with $\mathbf{D_Q}$ and $\mathbf{D_K}$ being -->

## Linear self-attention

Instead of approximating the attention matrix $\mathbf{A}$, the second paper directly approximates the result of dot-product attention using *linear attention*. First, they prove that dot-product attention is low-rank, and then propose to replace the $L \times L$ attention matrix with a $L \times k$ approximation by using a learned weight matrix $\mathbf{E} \in \mathbb{R}^{k \times L}$ to project $\mathbf{K}$ into $\mathbb{R}^{k \times d}$: 

$$
\mathbf{\hat{A}} = \operatorname{exp}\left(\frac{\mathbf{Q}(\mathbf{EK})^T}{\sqrt{d}}\right)
$$

Likewise, the values are also projected to $\mathbb{R}^{k \times d}$, and 

$$
\operatorname{\hat{Att}}(\mathbf{Q}, \mathbf{K}, \mathbf{V}) = \mathbf{\hat{D}}^{-1}\mathbf{\hat{A}FV}
$$

with  $\mathbf{F} \in \mathbb{R}^{k \times L}$ and

$$
\mathbf{\hat{D}}^{-1} = \operatorname{diag}(\mathbf{\hat{A}}\mathbf{1}_L)
$$

This requires $O(Lk)$ time. In practice, the authors find that $k \geq 256$ seems to perform well. 


## Discussion

Some random thoughts on these papers. 

- While both of these approximations perform comparably well to dot-product attention in the experiments presented in the papers, those experiments seem pretty perfunctory to me. I'd be more impressed if they demonstrated for a real problem that using one of these approximations opens up new possibilities. Concatenating random proteins together to length 8096 isn't a real problem!
- The FAVOR paper presents a general kernel framework for attention and investigate the performance of some simple kernels in their experiments. It'd be fun to try and design attention kernels for specific problem domains. 
- FAVOR makes a big deal about how they have an unbiased estimator for $\mathbf{A}$, but I'm pretty sure their $\operatorname{\hat{Att}}$ is not an unbiased estimator of dot-product attention. 
- The linear projections in linear self-attention ($\mathbf{E}$ and $\mathbf{F}$) are dependent on the sequence length, which would make dealing with variable-length inputs messy. 
