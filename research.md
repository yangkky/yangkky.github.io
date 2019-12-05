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

# Publications

**Machine learning-guided channelrhodopsin engineering enables minimally-invasive optogenetics.** Bedbrook CN, Yang KK, Robinson JE, Gradinaru V, Arnold FH. *Nature Methods,* October 14, 2019. [10.1038/s41592-019-0583-8](https://doi.org/10.1038/s41592-019-0583-8).

**Machine-learning-guided directed evolution for protein engineering.** Yang KK, Wu Z, Arnold FH. *Nature Methods*, July 15, 2019. [10.1038/s41592-019-0496-6](https://doi.org/10.1038/s41592-019-0496-6).

**"Batched stochastic Bayesian optimization via combinatorial constraints design."** Yang KK, Chen Y, Lee A, Yue Y. AIStats 2019. [arxiv](http://arxivs.org/abs/1904.08102).

**The Generation of Thermostable Fungal Laccase Chimeras by SCHEMA-RASPP Structure-Guided Recombination in Vivo.** Mateljak I, Rice A, Yang KK, Tron T, Alcalde M. *
*ACS Synthetic Biology,* March 21, 2019. [10.1021/acssynbio.8b00509](https://doi.org/10.1021/acssynbio.8b00509)

**"Learned protein embeddings for machine learning."** Yang KK, Wu Z, Bedbrook CN, Arnold FH. *Bioinformatics*. 23 March 2018.  [doi.org/10.1093/bioinformatics/bty178](https://academic.oup.com/bioinformatics/advance-article/doi/10.1093/bioinformatics/bty178/4951834?guestAccessKey=aa420938-7c4a-4c47-8763-bad82d936d10).

**“Machine learning to predict eukaryotic expression and plasma membrane localization of engineered integral membrane proteins.”** Bedbrook CN, Yang KK, Rice AJ, Gradinaru V, Arnold FH. *PLOS Computational Biology* 13(10): e1005786 (2017). [doi.org/10.1371/journal.pcbi.1005786](https://doi.org/10.1371/journal.pcbi.1005786).

**“Structure-Guided SCHEMA Recombination Generates Diverse Chimeric Channelrhodopsins.”**  C. N. Bedbrook, A. J. Rice, K. K. Yang, X. Ding, S. Chen, E. M. LeProust, V. Gradinaru, F. H. Arnold. *Proceedings of the National Academy of Sciences* 114, E2624-E2633 (2017). [doi/10.1073/pnas.170026911](https://doi.org/10.1073/pnas.1700269114).

# Preprints
**“Machine learning-guided channelrhodopsin engineering enables minimally-invasive optogenetics.”** Bedbrook CN, Yang KK, Robinson JE, Gradinaru V, Arnold FH. [biorXiv](https://doi.org/10.1101/565606).

**“Machine learning in protein engineering.”** Yang KK, Wu Z, Arnold FH. [arxiv](https://arxiv.org/abs/1811.10775).

# Presentations
**"Probabilistic protein engineering."** Janelia Research Center. 30 May 2019. 

**"Learning the language of proteins."** Gray-Hill Seminar, Occidental College. 29 June 2018.

**"Machine Learning to Predict Eukaryotic Expression and Plasma Membrane Localization of an Integral Membrane Protein."** Proteins Gordon Research Seminar. 18 June 2017.