---
layout: page
title: Research
permalink: /research/
---

# Current Research Interests

I am currently broadly interested in problems at the intersection of biology and machine learning. Some of my current interests include: 

- Generative models and pretraining for proteins and chemistry
- Machine learning for protein engineering
- Uncertainty quantification in neural networks


<!--# PhD Research

My PhD research used machine learning to attack challenges in protein engineering that are otherwise intractable because they are both too complex to be designed from first principles and not amenable to the high-throughput screens used in directed evolution. I collaborated with scientists both in the Arnold lab and in other groups to design enzymes and light-sensitive proteins with unique properties. I also worked on building sequence-function models tailored to biological sequences and on methods for using ML sequence-function models to guide directed evolution. 

## Machine-learning guided directed evolution

Directed evolution optimizes proteins through iterative diversification and screening without requiring knowledge of how the protein performs its function. The first step is sequence diversification from starting (parent) sequences. Second, screening and selection identifies variants with improved properties to start the next round of diversification. The process is repeated until fitness goals are reached.

![Directed evolution]({{ site.baseurl }}/assets/de_slide.png)

While effective (so much so that Frances won a Nobel Prize for it!), directed evolution has some limitations:

* It requires a starting point with measurable function
* It requires a high-throughput (>1000 sequence/week) screen

The second limitation arises because directed evolution discards all the information in the unimproved variants! If instead, we learn from that information, then we should be able to select new mutations more efficiently than by randomly mutating the current best variant, especially if the effects of mutations are not additive. I call this machine-learning guided directed evolution, and I wrote a whole [review](https://arxiv.org/abs/1811.10775) about it. Because reviews get stale very quickly in developing fields, I also maintain a [repository](https://github.com/yangkky/Machine-learning-for-proteins) listing papers covering machine learning on proteins. 

![Machine learning-guided directed evolution]({{ site.baseurl }}/assets/mlde_slide.png)

I've applied this approach to engineer channelrhodopsins (ChRs) for [membrane localization](https://doi.org/10.1371/journal.pcbi.1005786) in mammalian cells and to produce [stronger currents](https://www.biorxiv.org/content/10.1101/565606v1) across the cell membrane when activated by light. ChRs are often artificially expressed in neurons so that the neurons can be activated by shining lights on them, in a process known as optogenetics. We can only screen about 2 variants a week for the properties we care about, so traditional directed evolution doesn't work here!

In the second half of my PhD, I focused on developing methods for the two key steps in the machine learning-guided directed evolution process: the ML sequence-function model, and ML-guided selection for using that model to choose the next set of proteins to characterize. I developed a way to [learn vector representations](https://academic.oup.com/bioinformatics/article/34/23/4138/5042984) of proteins that leverages information in unlabeled sequences and a [method](https://arxiv.org/abs/1904.08102) for using information in a machine learning model to design site-saturation mutagenesis libraries. -->

# Publications

**Evolutionary velocity with protein language models.** Brian L. Hie, Kevin K. Yang, and Peter S. Kim. *Cell Systems*, 2022. [10.1016/j.cels.2022.01.003](https://doi.org/10.1016/j.cels.2022.01.003)

**Machine learning modeling of family wide enzyme-substrate specificity screens.**
Samuel Goldman, Ria Das, Kevin K Yang, Connor W Coley. *PLoS computational biology*, 2022. [10.1371/journal.pcbi.1009853](https://doi.org/10.1371/journal.pcbi.1009853)

**A topological data analytic approach for discovering biophysical signatures in protein dynamics.** Wai Shing Tang, Gabriel Monteiro da Silva, Henry Kirveslahti, Erin Skeens, Bibo Feng, Timothy Sudijono, Kevin K. Yang, Sayan Mukherjee, Brenda Rubenstein, Lorin Crawford. *PLoS computational biology*, 2022. [10.1371/journal.pcbi.1010045](https://doi.org/10.1371/journal.pcbi.1010045)

**Adaptive machine learning for protein engineering.** Brian L. Hie and Kevin K. Yang. C*urrent Opinion in Structural Biology*, 2022. [10.1016/j.sbi.2021.11.002](https://doi.org/10.1016/j.sbi.2021.11.002)

**FLIP: Benchmark tasks in fitness landscape inference for proteins.** Christian Dallago, Jody Mou, Kadina E. Johnston, Bruce J. Wittmann, Nicholas Bhattacharya, Samuel Goldman, Ali Madani, Kevin K. Yang. *NeurIPS 2021 Datasets and Benchmarks Track.* [10.1101/2021.11.09.467890](https://doi.org/10.1101/2021.11.09.467890)

**Protein sequence design with deep generative models.**  Zachary Wu, Kadina E. Johnston, Frances H. Arnold, and Kevin K. Yang. *Current Opinion in Chemical Biology*, 2021. [10.1016/j.cbpa.2021.04.004](https://doi.org/10.1016/j.cbpa.2021.04.004)

**Learned embeddings from deep learning to visualize and predict protein sets.** Christian Dallago, Konstantin Schütze, Michael Heinzinger, Tobias Olenyi, Maria Littmann, Amy X. Lu, Kevin K. Yang, Seonwoo Min, Sungroh Yoon, James T. Morton, Burkhard Rost. *Current Protocols,* May 2021. [10.1002/cpz1.113](https://doi.org/10.1002/cpz1.113)

**Signal Peptides Generated by Attention-Based Neural Networks.** Zachary Wu, Kevin K. Yang, Michael J. Liszka, Alycia Lee, Alina Batzilla, David Wernick, David P. Weiner, and Frances H. Arnold. *ACS Synthetic Biology*, 10 July 2020. [10.1021/acssynbio.0c00219](https://doi.org/10.1021/acssynbio.0c00219)

**Machine learning-guided channelrhodopsin engineering enables minimally-invasive optogenetics.** Bedbrook CN, Yang KK, Robinson JE, Gradinaru V, Arnold FH. *Nature Methods,* October 14, 2019. [10.1038/s41592-019-0583-8](https://doi.org/10.1038/s41592-019-0583-8).

**Machine-learning-guided directed evolution for protein engineering.** Yang KK, Wu Z, Arnold FH. *Nature Methods*, July 15, 2019. [10.1038/s41592-019-0496-6](https://doi.org/10.1038/s41592-019-0496-6).

**Batched stochastic Bayesian optimization via combinatorial constraints design.** Yang KK, Chen Y, Lee A, Yue Y. *AIStats 2019*. [arxiv](http://arxivs.org/abs/1904.08102).

**The Generation of Thermostable Fungal Laccase Chimeras by SCHEMA-RASPP Structure-Guided Recombination in Vivo.** Mateljak I, Rice A, Yang KK, Tron T, Alcalde M.
*ACS Synthetic Biology,* March 21, 2019. [10.1021/acssynbio.8b00509](https://doi.org/10.1021/acssynbio.8b00509)

**Learned protein embeddings for machine learning.** Yang KK, Wu Z, Bedbrook CN, Arnold FH. *Bioinformatics*. 23 March 2018.  [10.1093/bioinformatics/bty178](https://academic.oup.com/bioinformatics/advance-article/doi/10.1093/bioinformatics/bty178/4951834?guestAccessKey=aa420938-7c4a-4c47-8763-bad82d936d10).

**Machine learning to predict eukaryotic expression and plasma membrane localization of engineered integral membrane proteins.** Bedbrook CN, Yang KK, Rice AJ, Gradinaru V, Arnold FH. *PLOS Computational Biology* 13(10): e1005786 (2017). [10.1371/journal.pcbi.1005786](https://doi.org/10.1371/journal.pcbi.1005786).

**“Structure-Guided SCHEMA Recombination Generates Diverse Chimeric Channelrhodopsins.**  C. N. Bedbrook, A. J. Rice, K. K. Yang, X. Ding, S. Chen, E. M. LeProust, V. Gradinaru, F. H. Arnold. *Proceedings of the National Academy of Sciences* 114, E2624-E2633 (2017). [10.1073/pnas.170026911](https://doi.org/10.1073/pnas.1700269114).

# Preprints

**Exploring evolution-based &-free protein language models as protein function predictors.**
Mingyang Hu, Fajie Yuan, Kevin K. Yang, Fusong Ju, Jin Su, Hui Wang, Fei Yang, Qiuyang Ding. [arxiv](https://arxiv.org/abs/2206.06583)

**Masked inverse folding with sequence transfer for protein representation learning.**
Kevin K. Yang, Niccolò Zanichelli, Hugh Yeh. [biorxiv](https://doi.org/10.1101/2022.05.25.493516)

**Convolutions are competitive with transformers for protein sequence pretraining.** Kevin K. Yang, Alex X. Lu, Nicolo Fusi. [biorxiv](https://doi.org/10.1101/2022.05.19.492714)


**Randomized gates eliminate bias in sort-seq assays.**
Brian L. Trippe, Buwei Huang, Erika A. DeBenedictis, Brian Coventry, Nicholas Bhattacharya, Kevin K. Yang, David Baker, Lorin Crawford. [biorxiv](https://doi.org/10.1101/2022.02.17.480881)

<!--# Presentations

**"Signal Peptides Generated by Attention-Based Neural Networks."** GSK Data Forum. 16 Feb 2021. 

**"Signal Peptides Generated by Attention-Based Neural Networks"**. Boğaziçi University Biotech Conference. 15 Jan 2021. 

**"Machine optimization and generation of proteins"**. Ohio State University Society for Biological Engineering. 6 Nov 2020. 

**"Probabilistic protein engineering."** Janelia Research Center. 30 May 2019. 

**"Learning the language of proteins."** Gray-Hill Seminar, Occidental College. 29 June 2018.

**"Machine Learning to Predict Eukaryotic Expression and Plasma Membrane Localization of an Integral Membrane Protein."** Proteins Gordon Research Seminar. 18 June 2017.-->