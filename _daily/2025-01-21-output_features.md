---
layout: post
title: 2025-01-21
---

### Overlap between SAEs

Mostly worked on fixing the article and giving the final touches.


### Enhancing Automated Interpretability with Output-Centric Feature Descriptions. 

Read most of the paper. 

#### Summary

    The concept represented by a feature is determined by the causal role of that feaure in model behaviour 

Features are activated by imputs and lead to changes in outputs. 

Good feature descriptions should be output-centric instead of input centric.

The authors present 2 methods, what they call VocabProj (related to the logit lens) and one called TokenChange. Ensembling these methods with MaxAct gives better scores overall.  They propose output and input based evaluations.

For input based evaluations they use Generation scoring of feature explanations (described in  Rigorously assessing natural language explanations of neurons). You can measure if the average activation is higher in activating examples than in non activating examples. I would have done something like  $\frac{ \sum{activating_{positive}-activating_{neutral}}}{n_{examples}}$ 

For output based evaluations they generate 3 sets of text, one where the target features is clamped, and 2 where two random features are clamped (why 2?). Then they task the model to choose. 

To generate explanations they do logit lens on the decoder directions (VocabProj) and feature clamping followed by logit difference calculations (TokenChange). VocabProj is correlative and TokenChange is actually interventive. 

They make ensembles in multiple ways. Raw - where they concatenate information for both generation methods, or concatenate the already generated explanation.

#### Results

I want to comment on the results after I read them more carefully. 

#### Things I would do differently

- It seems that the way they defined the input based score does not give a single value for each latent but only an average value of the SAE. Defining it in a different way (like we did in the blog post) would be straight up better.
- The way they defined the output based evaluations uses 3 sets of text instead of just 2 (true feature and random feature) and it is not obvious to me if this does not leak information. It again only gives a binary signal per feature (accurate description or not) while it could also quantify it if they instead counted how many examples the scorer model got correctly (although that would probably lead to a more messy/confusing prompt/response)
- Token change is similar to what I was doing to extend Alex's output feature idea, although I restricted myself to activating examples on increasing/decreasing activations on tokens where the latent was already active
- They measure concatenated explanations and claim that summarized explanations perform worse; I think it is expected that concatenated explanations will have higher scores because they are longer/convey more information. Either way, concatenating explanations is worse than concatenating the information that the model uses to generate a single explanation

