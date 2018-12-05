---
layout: post
title: "Image Segmentation"
categories: [Study notes]
---

### Object proposal
Object proposals are regions of image (boxes or pixel segments) that are hypothesized (by some smart algorithm) to contain significant objects in the image. [source](https://www.quora.com/What-is-the-definition-of-Object-proposal-in-object-detection)

### Dense Prediction
In computer vision pixelwise dense prediction is the task of predicting a label for each pixel in the image

## Detection and Segmentation
<iframe src="https://drive.google.com/file/d/1xcvv7XymD1vx87AIS2yQD278tnPrM5iU/preview" width="100%" height="480"></iframe>
source: cs231n lecture 11 [link](https://www.youtube.com/watch?v=nDPWywWRIRo&t=370s)
### Semantic segmentation
Input an image and then output an decision of a category for every pixel in that image. Produce a category label for each pixel of the input image.

#### Semantic segmentation Idea: Sliding Window
Problem: very inefficient, not reusing shared features between overlapping patches.

#### Semantic segmentation Idea: Fully Convolutional
it's very expensive if the images are high resolution

* Design network as a bunch of convolutional layers, with downsampling and updampling inside the network.
* unpooling
  * nearest neighbor : duplicate
  * bed of nails unpooling : add 0
  * max unpooling : remember which element was max. use positions from pooling layer.
* Learnable unsampling: Transpose convolution

Giant convolutional network with downsampling and upsampling inside the network, downsampling will be by strided convolution or pooling, upsampling will be by transpose convolution, or various types of unpooling or unsampling.
We can train this whole thing end to end with back propagation using cross entropy loss over every pixel.

### Classification + Localization
### Object detection faster R-CNN
* Region proposal

### Instance Segmentation
Predict a whole segmentation mask for each of those objects and predict which pixels in the input image corresponds to each object instance.
mask R-CNN
