# DLC: Deep Learning Correspondence for Neuron ID

This tool was developed for automatically predicting neuron correspondence for point clouds of neurons. The point clouds do not requirestraightening or alignment as preprocessing. 

# Installation
The code was run in python 3.7 environment. The packages and version can be found in requirements.txt

# Usage
A template worm with labels already assigned is required. The data should be a python dictionary stored using pickle package with following keys:
1. pts: a numpy array of dimension N*3 as the xyz position of neurons(unit:micrometer)
2. fluo: a numpy array of dimension N*num_channel as the fluorescent signals.(Set to be None if not available)
3. name: a list of neuron names of length N as the name assigned to each neuron.

We predict the neuron names for a test worm, which is also a python dictionary stored with pickle. The dictionary contains 2 keys:
1. pts: a numpy array of dimension M*3 as the xyz position of neurons(unit:micrometer)
2. fluo: a numpy array of dimension M*num_channel as the fluorescent signals.(Set to be None if not available)

An example of template and test worm is provided in Data/Example

To run the ID prediction, use the predict function in DLE_predict.py. An example of running code was provided in src/example.ipynb 

