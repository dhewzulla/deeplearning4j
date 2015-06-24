---
title: 
layout: default
---

# Deep-Belief Networks

For our purposes, a deep-belief network can be defined as a stack of restricted Boltzmann machines in which each layer communicates with both the previous and subsequent layers. The nodes of any single layer don't communicate with each other laterally. 

With the exception of the first and final layers, each hidden layer has a double role: it serves as the hidden layer to the higher nodes that come before it, and as the input (or visible) layer to the lower nodes that come after. It is a network of single-layer networks. 

Deep-belief networks are used to recognize and generate images, video sequences and motion-capture data. A continuous deep-belief network is simply an extension of a deep-belief network that accepts a continuum of decimals, rather than binary data. 

### Parameters & k

See the [parameters common to all multilayer networks](../multinetwork.html).

The variable k is the number of times you run [contrastive divergence](../glossary.html#contrastivedivergence). Each time contrastive divergence is run, it's a sample of the Markov chain. In composing a deep-belief network, a typical value is one.

### Initiating a Deep-Belief Network

Traverse the input data with the IrisDataSetInterator.

<script src="http://gist-it.appspot.com/https://github.com/deeplearning4j/dl4j-0.0.3.3-examples/blob/master/src/main/java/org/deeplearning4j/deepbelief/DBNIrisExample.java?slice=57:62"></script>

Configure the DBN as a MultilayerNeuralNet whose layers are RBMs:

<script src="http://gist-it.appspot.com/https://github.com/deeplearning4j/dl4j-0.0.3.3-examples/blob/master/src/main/java/org/deeplearning4j/deepbelief/DBNIrisExample.java?slice=42:98"></script>

Then evaluate the performance of the net:

<script src="http://gist-it.appspot.com/https://github.com/deeplearning4j/dl4j-0.0.3.3-examples/blob/master/src/main/java/org/deeplearning4j/deepbelief/DBNIrisExample.java?slice=107:122"></script>

Note that the *eval* class combines [confusion matrices](../glossary.html#confusionmatrix) and f1 scores to allow for easy display and evaluation of data. This is useful for tracking how well your network trains over time. 

F1 scores are expressed as percentages. They are basically the probability that your net's guesses are correct. To improve the performance of nets, you can tune them by modifying the number and size of the hidden layers, and tweaking other parameters such as learning rate, momentum, weight distribution and various types of regularization.

Next, we'll show you how to use [distributed and multithreaded computing](../scaleout.html) to train your networks more quickly. To read about another type of deep net, the deep autoencoder, [click here](../deepautoencoder.html). 