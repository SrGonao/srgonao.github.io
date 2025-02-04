---
layout: post
title: 2024-12-15
---

### Intro

I've decided that I wanted to have a daily journal where I write down what I've done during the research day. It will be mostly unstructured, probably not very coherent but will be a good source for more structured outputs.

I will probably be sharing results directly here, some of them probably wrong. Because I'm going to be updating this daily, hopefully this creates a record of things that become less wrong over time.

Setting this page/website was harder than I expected.


### Results 


Training for less tokens makes seeds less aligned. Does aligment converge at a certain number of tokens?

Increasing the k in top-k decreased alignment between seeds instead of increasing it as I expected. Nora mentioned that if the SAE was dense then we would expect to be no alignment between seeds, so that could make sense. 

Still don't have results for other models, but what we are seeing seems to hold. 

Probably it is the case that top-k is the origin of the misaligment between seeds, but still need to run the standard l1 and gated sae experiments to confirm. Seem to have good hyperparameters for those experiments as well. 








