---
layout: page
title: Research
permalink: /research/
---

Machine learning is the science of getting computers to learn from data instead of being explicitly programmed. In the past decade, machine learning has given us machine translation, self-driving cars, and effective web search. As DNA-sequencing and synthesis technology improves, humanity is amassing a vast collection of biological sequence data. Machine learning will be a vital approach for understanding and using this data.

My PhD research used machine learning to attack challenges in protein engineering that are otherwise intractable because they are both too complex to be designed from first principles and not amenable to the high-throughput screens used in directed evolution. I collaborated with scientists both in the Arnold lab and in other groups to design enzymes and light-sensitive proteins with unique properties. I also worked on building sequence-function models tailored to biological sequences and on methods for using ML sequence-function models to guide directed evolution. 

# Machine-learning guided directed evolution

Directed evolution optimizes proteins through iterative diversification and screening without requiring knowledge of how the protein performs its function. The first step is sequence diversification from starting (parent) sequences. Second, screening and selection identifies variants with improved properties to start the next round of diversification. The process is repeated until fitness goals are reached.

![Directed evolution]({{ site.baseurl }}/assets/de_slide.png)

While effective (so much so that Frances won a Nobel Prize for it!), directed evolution has some limitations:

* It requires a starting point with measurable function
* It requires a high-throughput (>1000 sequence/week) screen

The second limitation arises because directed evolution discards all the information in the unimproved variants! If instead, we learn from that information, then we should be able to select new mutations more efficiently than by randomly mutating the current best variant, especially if the effects of mutations are not additive. I call this machine-learning guided directed evolution, and I wrote a whole [review](https://arxiv.org/abs/1811.10775) about it. Because reviews get stale very quickly in developing fields, I also maintain a [repository](https://github.com/yangkky/Machine-learning-for-proteins) listing papers covering machine learning on proteins. 

![Machine learning-guided directed evolution]({{ site.baseurl }}/assets/mlde_slide.png)

I've applied this approach to engineer channelrhodopsins (ChRs) for [membrane localization](https://doi.org/10.1371/journal.pcbi.1005786) in mammalian cells and to produce [stronger currents](https://www.biorxiv.org/content/10.1101/565606v1) across the cell membrane when activated by light. ChRs are often artificially expressed in neurons so that the neurons can be activated by shining lights on them, in a process known as optogenetics. We can only screen about 2 variants a week for the properties we care about, so traditional directed evolution doesn't work here!

In the second half of my PhD, I focused on developing methods for the two key steps in the machine learning-guided directed evolution process: the ML sequence-function model, and ML-guided selection for using that model to choose the next set of proteins to characterize. I developed a way to [learn vector representations](https://academic.oup.com/bioinformatics/article/34/23/4138/5042984) of proteins that leverages information in unlabeled sequences and a [method](https://arxiv.org/abs/1904.08102) for using information in a machine learning model to design site-saturation mutagenesis libraries. 