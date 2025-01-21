---
layout: post
title: 2025-01-13
---


# SAE overlap of interpretations

Explanations are more aligned if you use the decoder/encoder alignment (didn't try encoder actually). 

For some reason aligning the embedding vectors lead to worse alignment (need to double check this). 

There's a big overlap of explanations between latents (mean alignment and max alignment are very different)

# Transcoder interpretability 

Transcoders on all model sizes tried are more interpretable than MLP SAEs.

They also have worse explainability as the model gets bigger. 

Very small sparse networks suck and are not really interpretable, not sure what to make of that.


