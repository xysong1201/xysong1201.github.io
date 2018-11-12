---
layout: post
title: "Paper review #2: DeepNAT Feb.2017 "
---

### DeepNAT: Deep Convolutional Neural Network
* 3-D patch based.
* Predict the central and the neighbors voxel of the patch.(Multi-task approach)
* 2 Netwroks hierarchically: separates foreground from background; identify 25 brain structures on the foreground.
* Indroduce intrinsic parameterization of the brain volume, formed by eigenfunctions of the Laplace-Beltrami operator to define the spatial context.

### Network Architecture
* 3 convolutional layers with pooling, bathch normalization, and non-linearities, followed by fully connected layers with dropout.
* 2.7 million parameters
