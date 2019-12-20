---
layout: post
title: "NeurIPS workshops and reflections"
date: 2019-12-19 00:00:00 -0800
---

NeurIPS was my second ML conference (after AISTATS). Attending with co-workers, having people reach out to set up meetings (and respond to my requests for meetings), and running into people from AISTATS really made me feel much more a part of the community even though the conference was much bigger. 

See previous posts ([1](https://yangkky.github.io/2019/12/10/neurips-day-1.html), [2](https://yangkky.github.io/2019/12/12/neurips-day-2.html), [3](https://yangkky.github.io/2019/12/13/neurips-day-3.html)) for thoughts on the first three days. 

## Themes and observations

### Unexpected companies venturing into biology

The Expo only had two biotech companies (BenevolentAI and Novartis), but there are some unexpected companies interested in machine learning on proteins. I talked to scientists or saw papers from Google, Salesforce, Amazon, and Facebook. It will be interesting to see whether this remains a fun side-project for scientists at big tech companies, or if they'll be making bigger investments. 

### How people spend their time

In general, the talks are not as full as you'd expect given the scale of the conference. Relatedly, multiple people have told me that their strategy for NeurIPS is to mostly ignore the talks and meet with friends and colleagues new and old. With that said, the keynotes do tend to fill up, and the poster sessions were basically science mosh pits. 

### Machine learning beyond black-box predictive accuracy

I noticed a lot of momentum in expanding deep learning and machine learning beyong achieving high predictive accuracy. I have a particular soft spot for all the work on Bayesian deep learning and uncertainty quantification, and the first half of the BDL workshop was a definite highlight. Yoshua Bengio gave a keynote on how the field needs to move to models with stronger "consciousness" priors that generalize better to unseen situations. This would out of distribution generalization and transfer would be the first step towards higher-level cognition and agents with internal world models that can reason about causality and seek out knowledge. 

There's also a lot more (and very necessary) interest in fairness, ethics, and safety. I missed the opening keynote, but moving from not wanting to change the conference name to having an opening keynote mention the #MeToo movement is encouraging. There were workshops on safety, climate change, and fairness in healthcare. 

## Interesting workshop papers and posters

[**Biological Sequence Design using Batched Bayesian Optimization**](https://ml4physicalsciences.github.io/files/NeurIPS_ML4PS_2019_141.pdf)  
David Belanger, Suhani Vora, Zelda Mariet, Ramya Deshpande, David Dohan, Christof Angermueller, Kevin Murphy, Olivier Chapelle, Lucy Colwell.  
You know your subfield is getting popular when Kevin Murphy shows up on the author list. Well-done overview of some of the difficulties of applying Bayesian optimization to biological sequences, with comparisons between some methods. 

[**Wat heb je gezegd? Detecting Out-of-Distribution Translations with Variational Transformers**](http://bayesiandeeplearning.org/2019/papers/90.pdf)  
Tim Z. Xiao Aidan N. Gomez Yarin Gal.  
Comes up with a way to estimate epistemic uncertainty on sequence predictions and some good ideas on how to measure the quality of an uncertainty measure. 

[**Deep Mean Functions for Meta-Learning in Gaussian Processes**](https://arxiv.org/abs/1901.08098)  
Vincent Fortuin, Gunnar Rätsch.  
Using a NN for the mean function in a GP seems like it should lead to better performance, but maximizing the marginal likelihood leads to overfitting because the marginal likelihood does not regularize the hyperparameters of the mean function. We can get around that by using meta-learning to learn a prior mean parameterized by a NN. This seems related to [neural processes](https://arxiv.org/abs/1807.01622). 

[**Reconstructing continuous distributions of 3D protein structure from cryo-EM images**](https://arxiv.org/abs/1909.05215)  
Ellen D. Zhong, Tristan Bepler, Joseph H. Davis, Bonnie Berger.  
Recent advances in hardware have enabled much higher resolution cryo-EM structures. However, most protein structure work ignores the fact that proteins exist as dynamic ensembles of structures. This work uses a VAE to reconstruct the entire ensemble from cryo-EM images. 


### Personal lessons

- Walking up to people I don't know is very hard and stressful, but if I set up an appointment with somebody, then talking to them isn't stressful at all. 
- However, having conversations in two emails, Twitter, Whova, FB messenger, SMS, and WeChat all going at once *is* a little stressful. 
- I wish I'd contacted more non-bio people doing work I'm interested in. All the ones I talked to were delightful! 
