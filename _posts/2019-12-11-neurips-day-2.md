---
layout: post
title: "NeurIPS Day 2"
date: 2019-12-11 21:00:00 -0800
---

Today started with a meetup for Boston-area people. It's always a little strange to fly across the continent to meet with people from the same city, but it was really fun to meet people who I could concievably easily see again. In my past conferences, I haven't really known anybody and would often wander around awkwardly at mealtimes, so I've gone a little bit overboard this time with setting up meals with people beforehand. It also helps that people are starting to reach out to me asking to meet. End result is that I've gotten to meet a lot of interesting people the last couple days, including: 

- [Trenton Bricken](https://twitter.com/TrentonBricken)
- [Jonathan Niles-Weed](https://www.jonathannilesweed.com/)
- [Amy Lu](https://twitter.com/amyxlu)
- [Alex Lu](https://twitter.com/alexijielu)
- [Alan Moses](http://www.moseslab.csb.utoronto.ca/)
- [Philip Paquette](https://ppaquette.io/)
- [David Yang](https://twitter.com/davidkmyang)
- [Sam Sinai](https://twitter.com/samsinai)
- [Elīna Locāne](https://twitter.com/elooopy?lang=en) 
- [Neil Thomas](https://twitter.com/countablyfinite?lang=en)
- [Roshan Rao](https://rmrao.github.io/)
- [Nicholas Bhattacharya](https://nickbhat.github.io/)

I also ran into [Neil Lawrence](https://inverseprobability.com/) in the elevator and [Andreas Krause](https://las.inf.ethz.ch/krausea) in front of a poster today. I recognized Neil's voice from [Talking Machines](https://www.thetalkingmachines.com/). I've worked with several people who had previously worked with Andreas Krause, and refer to a few of his papers frequently, so I was very excited to hear that he'd read one of my papers. 

## Some papers I think are interesting

[**The Cells Out of Sample (COOS) dataset and benchmarks for measuring out-of-sample generalization of image classifiers**](https://arxiv.org/abs/1906.07282)  
Alex X. Lu, Amy X. Lu, Wiebke Schormann, Marzyeh Ghassemi, David W. Andrews, Alan M. Moses.  
Neural networks often learn confounders in biological data, such as the day of the experiment, the facility, or the position in a plate. The COOS dataset tests classifier performance when generalizing across these effects. Surprisingly, a vanilla supervised learner generalizes better than pre-trained models.  
![COOS]({{ site.baseurl }}/assets/coos.png)  

[**Single-Model Uncertainties for Deep Learning**](https://arxiv.org/abs/1811.00908)  
Natasa Tagasovska, David Lopez-Paz.  
Separately model aleatoric uncertainty using quantile regression and epistemic uncertainty by training a classifier to predict whether test examples are from the training distribution. 

[**Image Synthesis with a Single (Robust) Classifier**](https://arxiv.org/abs/1906.09453)  
Shibani Santurkar, Dimitris Tsipras, Brandon Tran, Andrew Ilyas, Logan Engstrom, Aleksander Madry.  
If you make your image classifier robust to adversarial examples, you can use it to generate realistic samples. 

[**Adaptive Sequence Submodularity**](https://arxiv.org/abs/1902.05981)  
Marko Mitrovic, Ehsan Kazemi, Moran Feldman, Andreas Krause, Amin Karbasi.  
Problems that involve finding the optimal ordering of edges in a graph, such as choosing the order in which to recommend movies or video games, turn out to be submodular. Therefore, once the graph is computed, the order can be greedily optimized with strong optimality guarantees.  
![adaptive sequence submodularity]({{ site.baseurl }}/assets/adaptive-submodularity.png)  

[**Computing Full Conformal Prediction Set with Approximate Homotopy**](https://arxiv.org/abs/1909.09365)  
Eugene Ndiaye, Ichiro Takeuchi.  
Transductive conformal regression traditionally involves calculating conformal scores for an intractible number of possible predictions. We can get around that by making some assumptions about the smoothness of the underlying predictive function. This results in slightly looser prediction intervals but maintains validity. Unlike inductive conformal regression methods, there's no need to split the training data into a proper training set and a conformal scoring set. 

