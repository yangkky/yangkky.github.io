---
layout: post
title: "Reflections on AIStats2019"
date: 2019-05-15 00:00:00 -0800
---
 
Towards the end of my PhD, I decided to pivot my research more towards machine learning (with an emphasis on proteins) instead of protein engineering (with an eye towards machine learning). As part of that pivot, I worked really hard with some awesome collaborators and got a [paper](https://arxiv.org/abs/1904.08102) accepted to [AIStats](https://www.aistats.org/). I was fortunate that [Yisong Yue](http://www.yisongyue.com/) and my new company were willing to fund my attendance, and so off I went to Naha, Okinawa. 

AIStats was my first ML/AI conference, and it was very enjoyable to be at a conference in the field that I consider my new intellectual home. A few talks, especially those on optimization, were over my head, I was able to track with nearly every paper presented. While I've enjoyed the previous conferences I've been to, I definitely found the research at this one the most interesting and stimulating.

Although the conference was in Okinawa, almost everybody I met came from either California or Boston. Going halfway around the world is apparently exactly the impetus I need to meet people who live and work within 5 miles of me. 

### Themes and observations

I saw a lot of work on optimal transport, Gaussian processes, and bandits. I've been inspired to read up on [optimal transport](https://arxiv.org/abs/1803.00567), which underpins a lot of recent theoretical work in machine learning. The bandit people definitely have the best names for things (rotting bandits! decaying bandits!). It's just too bad the main application seems to be ad serving. AIStats is definitely has a more theoretical focus than the other major conferences: you won't find much benchmark chasing here or many gigantic neural networks here.

Perhaps not surprisingly, only 13.1% of participants were female, and only 8% were from Japan. Assuming independence, the expected number of Japanese women participants would have been around 5. I didn't see any. Perhaps relatedly, a female graduate [student](https://www.linkedin.com/in/sunipa-dev-a12906126/) gave a very nice talk on [attenuating bias in word vectors](http://proceedings.mlr.press/v89/dev19a/dev19a.pdf), and the first question (more of a comment) was fittingly an older white man stating that gender and racial biases are present in the data and so it's not a problem that they're encoded in word vectors.


### Interesting papers

**Structured Disentangled Representations.**  
Babak Esmaeili, Hao Wu, Sarthak Jain, Alican Bozkurt, N Siddharth, Brooks Paige, Dana H. Brooks, Jennifer Dy, Jan-Willem Meent.  
[[PDF](http://proceedings.mlr.press/v89/esmaeili19a/esmaeili19a.pdf)]  
The authors derive a hierarchical objective in order to explicitly represent the trade-offs between mutual information between data and representation, KL divergence between representation and prior, and coverage of the support of the empirical data distribution. This allows them to learn representations that disentangle both discrete and continuous (input) variables. 

**Fast and Robust Shortest Paths on Manifolds Learned from Data.**  
Georgios Arvanitidis, Soren Hauberg, Philipp Hennig, Michael Schober.  
[[PDF](http://proceedings.mlr.press/v89/arvanitidis19a/arvanitidis19a.pdf)]  
The authors derive an ODE-based method for computing shortest paths and distances on Riemannian manifolds learned from data. This may have implications for using neural networks for design or for interpolation between data points.

**Resampled Priors for Variational Autoencoders.**  
Matthias Bauer, Andriy Mnih.  
[[PDF](http://proceedings.mlr.press/v89/bauer19a/bauer19a.pdf)]  
The standard normal prior used in VAEs leads to underfitting. Using Learned Accept/Reject Samplings to construct a richer prior during or after VAE training improves samples from the VAE. This is one of a few recent papers demonstrating methods for improving the VAE prior in order to get better samples.

**On Multi-Cause Approaches to Causal Inference with Unobserved Counfounding: Two Cautionary Failure Cases and A Promising Alternative. Proceedings of Machine Learning Research**.  
Alexander D’Amour.  
[[PDF](http://proceedings.mlr.press/v89/d-amour19a/d-amour19a.pdf)]  
Alex gave a very engaging and easy-to-follow talk on why the typical approaches to causal inference over several variables simultaneously cannot succeed. Most of the talk was about how the things we'd like to do are impossible, but it didn't come off as overly negative or pessimistic. 

**Deep learning with differential Gaussian process flows.**  
Pashupati Hegde, Markus Heinonen, Harri Lähdesmäki, Samuel Kaski.  
[[PDF](http://proceedings.mlr.press/v89/hegde19a/hegde19a.pdf)]  
A very elegant follow-up to *Neural Ordinary Differential Equations.* Basically, use deep GPs to warp your input space until you can get good accuracy with a linear model on top. Interestingly, Markus Heinonen, Harri Lähdesmäki are authors on *[mGPFusion](https://academic.oup.com/bioinformatics/article/34/13/i274/5045756)*, which is one of my favorite ML-for-proteins papers.

**Gaussian Process Latent Variable Alignment Learning.**  
Ieva Kazlauskaite, Carl Henrik Ek, Neill Campbell.  
[[PDF](http://proceedings.mlr.press/v89/kazlauskaite19a/kazlauskaite19a.pdf)]  
Use separate GPs to simultaneously align warped time series and learn the underlying time series functions. I was hoping that this would generalize to discrete sequences, but it doesn't seem to very easily. Nevertheless, this is a very cool Bayesian method, although I would have loved to see a full Hamiltonian Monte Carlo treatment of the posteriors. 

### Personal lessons

- The best way to meet people as an introvert is to hang out with extroverted or well-connected people and let them introduce you to all their friends. 
- It's ok to plan to go back to the room and rest at some point during the day. It's better to be 100% present and ready to engage for most of the day than to be running on dregs the whole time. 
- This post would have been much better if I'd taken notes on my impressions of the conference itself instead of just on papers I thought were interesting. After all, the papers will still be there to read later!