# fDNC: fast Deep Neural Correspondence

This tool was developed for automatically predicting neuron correspondence between two point clouds of neurons. User can freely choose their favorite segmentation algorithm to detect neurons(point cloud) from fluorescence images. This algorithm does not require straightening or axis-alignment of the worm head as preprocessing step. 

# Installation
The code was run and tested in a python 3.7 environment. The packages and their version can be found in requirements.txt

# Usage
The code can be run with or without an Nvidia GPU. The default setting is to run with GPU, and set the argument cuda=False makes the model be run with CPU. The running speed with a Intel(R) Xeon(R) Gold 6148 CPU @ 2.40GHz is 0.05s/worm.

The model requires two inputs:

A template worm with labels already assigned is required. In the example code, the template worm input is a python dictionary with the following keys:
1. pts: a NumPy array of dimension N*3 as the XYZ position of neurons(unit: micrometer)
2. fluo: a NumPy array of dimension N*num_channel as the fluorescent signals.(Set to be None if not available)
3. name: a list of neuron names of length N as the name assigned to each neuron.

A test worm is also a python dictionary. This dictionary contains 2 keys:
1. pts: a NumPy array of dimension M*3 as the XYZ position of neurons(unit: micrometer)
2. fluo: a NumPy array of dimension M*num_channel as the fluorescent signals. (Set to be None if not available)

Each recorded worm is unstraightened and the head direction is arbitrary. The recorded worms tested in this work lie on their right sides.(For a worm that lies on its left side, we can simply rotate 180 degrees by inverting the sign of x and z coordinates). 

An example of input data of a template and a test worm is provided in folder Data/Example

# Example Code
To run the ID prediction, use the predict function in src/DNC_predict.py. An example of how to use it is provided in src/example.ipynb 

# Pretrain model
We provide a pretrained model and recommend our user to download the pretrained model and save it in the model folder as model/model.bin. The model can be found at <a href="https://osf.io/t7dzu/">Data And Pretrained Model</a>

We also provide the code for training the model with synthetic data. An example for training with your own train and validation set is as follows:
```
python ./src/fDNC_train.py --train_path ./Data/train --eval_path ./Data/val
```
We also provide our training data at <a href="https://osf.io/t7dzu/">Data And Pretrained Model</a>

