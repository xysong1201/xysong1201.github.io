---
layout: post
title: "Paper review #1: QuickNAT Jan.2018 "
---

### QuickNAT : A deep fully convolution neural network (F-CNN) 
* First, apply FreeSurfer to segment scans without annotations.
* Second, fine-tune the previous network with the limited manually annotated data.

### Conclusion
* The fully convolutional architecture offers faster processing and lager context than path-based DeepNAT.
* The dense connections within every encoder and decoder block promote feature re-usibility in the network.

### Architecture of the network
* 4 encoders, 4 decoders separated by a bottleneck layer
* Skip connections between all encoder and decoder blocks of the same spatial resolution
* Each dense block consistes of 3 convolutional layers. Every convolutional layer is preceded by a batch-normalization layer and a ReLU layer. The first 2 convolutional layers are followed by a concatenation layer. (dense connections))
* The kernel size for these 2 convolutional layers is kept small (5x5)
* Output channels for each convolution layer is set to 64
* The third convolutional layer has a 1x1 kernel size.
* The classifier block is basically a convolutional layer with 1x1 kernel size, which maps the input to an N channel feature map, N is the number of class. This is followed by a soft-max layer to map the activations to probabilities.

### Loss function
* QuickNAT is learnt by optimizing 2 loss functions simultaneoulsy: weighted logistic loss; multi-class Dice loss.

### Model learning
* lr = 0.1; Reduced by one order after every 10 epochs.
* weight decay term = 0.0001
* Batch size = 4
* momentum = 0.95

### Training with Limited Annotated data

#### 1. Pretraining on large unlabeled datasets with auxiliary labels
* Use a large neuroimaging dataset: ([IXI dataset](http://brain-development.org/ixi-dataset/)), apply FreeSurfer to obtain auxiliary segmentations.
* Pretrain QuickNAT on this large dataset with auxiliary labels.

#### 2. Fine-tuning with limited manually labelled data
* Use data from the Multi-Atlas Labelling Challenge dataset (Landman and Warfield,2012)
* lr = 0.01; reduce it by an order after every 5 epochs until convergence
