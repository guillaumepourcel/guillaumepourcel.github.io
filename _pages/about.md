---
layout: about
title: about
permalink: /

profile:
  align: right
  image: prof_pic.jpg


news: true  # includes a list of news items
selected_papers: true # includes a list of papers marked as "selected={true}"
social: true  # includes social icons at the bottom of the page
---



I am a PhD candidate in the AI department at the [University of Groningen](https://www.rug.nl/), where I work in the [MINDS](https://www.ai.rug.nl/minds/) group under the supervision of [Prof. Herbert Jaeger](https://scholar.google.com/citations?hl=en&user=0uztVbMAAAAJ&view_op=list_works). My research is affiliated with [CogniGron](https://www.rug.nl/research/fse/cognitive-systems-and-materials/?lang=en) and supported by the [Post-Digital](http://postdigital.astonphotonics.uk/) project. Throughout my doctoral studies, I have been a visiting researcher at [ETH Zurich](https://ethz.ch/en.html) and [IFISC](https://ifisc.uib-csic.es/), and completed research internships at [Inria (SCOOL)](https://www.inria.fr/en/scool) and [Inria (Flowers)](https://flowers.inria.fr/). I also collaborated with [Maxence Ernoult](https://scholar.google.com/citations?user=wGB7cpUAAAAJ&hl=fr) from Google DeepMind. 

#### Research Interests

**Hardware-aware learning algorithms** Modern computing is increasingly dominated by just two operations: neural network inference and gradient computation. This demands exploiting the specificities of these two programs through specialized hardware. Going further, it was proposed to redesign them so that they are intrinsically unified into a single process. This was called ["physics-grounded deep learning"](https://umontreal.scholaris.ca/items/f5292d56-6175-4300-bfd9-e2d71f713b13), with algorithms like [equilibrium propagation](https://www.frontiersin.org/journals/computational-neuroscience/articles/10.3389/fncom.2017.00024/full) where inference and gradient computation are done with the same physical process. However, these methods were limited to equilibrium systems that can only process static data—missing the temporal sequences that dominate real-world applications.

My research addresses this gap through [RHEL](https://arxiv.org/abs/2506.05259) (Recurrent Hamiltonian Echo Learning), which extends physics-grounded learning to dynamical systems. RHEL computes exact gradients through time using the same forward dynamics—no separate backward pass or memory storage needed. This makes it naturally suited for analog and neuromorphic hardware where both inference and learning obey the same physical process, potentially achieving better efficiency than its conventional autodiff counterpart (backpropagation through time).

**Agency in AI systems** My cognitive science background drove my interest in the fundamental gap between natural and artificial agency. Current approaches to agentic AI fall into two inadequate categories: rigid hand-engineered reward functions in RL, or the poorly-understood emergent behaviors of LLMs that mimic human motivations from training corpora—often with systematic pathologies. Understanding and bridging this gap is crucial for building AI systems that can act autonomously in complex, open-ended environments.
My contributions to this problem include studies on:
- Persuasion as an intrinsic motivation for training LLMs.
- Interest-based curriculum learning for Deep RL

