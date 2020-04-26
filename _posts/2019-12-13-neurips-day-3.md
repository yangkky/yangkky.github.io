---
layout: post
title: "NeurIPS Day 3"
date: 2019-12-13 07:00:00 -0800
---

I spent most of today meeting with friends and colleagues new and old. I think everybody from my company is here now, but I still haven't seen some of them because this place is so big. It's also nice to see some Arnold lab representation from [Zach Wu](https://twitter.com/zvxywu?lang=en) and [Kadina Johnston](https://www.linkedin.com/in/kadina-johnston). 

## Ethics at NeurIPS

There are a few papers here with clear ethical issues. For example: 

![political-bias]({{ site.baseurl }}/assets/political-bias.jpeg)  

Also see [this](https://twitter.com/hannes_brt/status/1205380141385338880)

The worst part is that a lot of these are trying to extract information that we have no reason to believe exists in the data.

And no, rejecting papers for ethical reasons is no more censorship than is rejecting papers for poor methodology. In other fields, certain topics or experiments require ethical review before doing the work, and publications won't even review papers that were done without this initial approval. 

## Some papers I think are interesting

Not as many papers today because I was too tired to do as much pushing through crowds at the poster session. 

[**Thompson Sampling and Approximate Inference**](https://arxiv.org/abs/1908.04970)  
My Phan, Yasin Abbasi-Yadkori, Justin Domke.  
Variational inference is much faster than exact methods for computing Bayesian posteriors, but even small errors in the approximate posteriors lead to very poor performance (linear regret) when they are used in Thompson sampling. If the posterior estimates are under-dispersed, forced exploration can restore strong performance. 

[**Can Unconditional Language Models Recover Arbitrary Sentences?**](https://arxiv.org/abs/1907.04944)  
Nishant Subramani, Sam Bowman, Kyunghyun Cho  
Given a language model decoder and a sentence, we can find an encoding that reconstructs the sentence perfectly when passed through the decoder. 

[**Practical Two-Step Look-Ahead Bayesian Optimization**](https://papers.nips.cc/paper/9174-practical-two-step-lookahead-bayesian-optimization.pdf)
Jian Wu, Peter I. Frazier.  
Bayesian optimization algorithms typically only look one step ahead during the acquisition function because methods that look two or more steps ahead are either too expensive or too inaccurate to be useful. This paper combines a few techniques to make accurate two-step look-ahead feasible. 