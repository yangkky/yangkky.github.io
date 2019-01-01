---
layout: page
title: Research
permalink: /research/
---
# Machine-learning guided directed evolution

Directed evolution optimizes proteins through iterative diversification and screening without requiring knowledge of how the protein performs its function. The first step is sequence diversification from starting (parent) sequences. Second, screening and selection identifies variants with improved properties to start the next round of diversification. The process is repeated until fitness goals are reached.

![Directed evolution]({{ site.baseurl }}/assets/de_slide.png)

While effective (so much so that Frances won a Nobel Prize for it!), directed evolution has some limitations:

* It requires a starting point with measurable function
* It requires a high-throughput (>1000 sequence/week) screen

The second limitation arises because directed evolution discards all the information in the unimproved variants! If instead, we learn from that information, then we should be able to select new mutations more efficiently than by randomly mutating the current best variant, especially if the effects of mutations are not additive. I call this machine-learning guided directed evolution, and I wrote a whole [review](https://arxiv.org/abs/1811.10775) about it.

![Machine learning-guided directed evolution]({{ site.baseurl }}/assets/mlde_slide.png)

I've applied this approach to engineer channelrhodopsins (ChRs) for [membrane localization](https://doi.org/10.1371/journal.pcbi.1005786) in mammalian cells and to produce stronger currents across the cell membrane when activated by light. ChRs are often artificially expressed in neurons so that the neurons can be activated by shining lights on them, in a process known as optogenetics. We can only screen about 2 variants a week for the properties we care about, so traditional directed evolution doesn't work here!

In the second half of my PhD, I focused on developing methods for the two key steps in the machine learning-guided directed evolution process: the ML sequence-function model, and ML-guided selection for using that model to choose the next set of proteins to characterize.

# Vector representations of proteins

The first step of a machine-learning pipeline for proteins is *encoding* the proteins. In the channelrhodopsin work, we used what's known as a one-hot encoding. For example, if I want to encode the DNA sequence AGTT, then I can encode each position using three 0s and one 1. Of course, for proteins, I would need 19 zeros and one 1 for each position.

![One-hot encoding]({{ site.baseurl }}/assets/onehot.jpg)

One-hot encodings are a good default. They do, however, have some drawbacks. One-hot encodings are space-inefficient and don't account for the amino acid properties. There are lists and tables of amino acid properties, but different problems will require different properties, and it's not obvious beforehand what those are. In general, we may also want to incorporate information from uncharacterized protein sequences into our model, as they may inform us about what makes a protein a protein (instead of just a random sequence of amino acids). So if we're training models to predict protein properties from data, why not train models to encode the proteins too?

The general idea is to grab a bunch of protein sequences from a database and use them to train an embedding model that maps from protein sequences to a vector space. This model can then be used to embed specific sequences of interest in that vector space as a pre-processing step before training the supervised model that learns how sequence determines function.

![Unsupervised-supervised]({{ site.baseurl }}/assets/unsupervised-supervised.png)

I talk more in-depth about one specific way to implement this [here]({{ site.baseurl }}/2018/03/26/learning-the-language-of-proteins.html).
