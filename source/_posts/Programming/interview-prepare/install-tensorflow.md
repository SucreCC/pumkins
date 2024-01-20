---
title: How to install tensorflow
sticky: true
date: 2024-1-20 20:02:00
layout: categories
categories:
- [Blog]
tags:
- Sucre
- machine learning
- tensorflow
- install
---

How to install tensorflow in macOS by pip



<!-- more -->

# Install

```` Bash
python3 -m venv tensorflow
pip install --upgrade pip
pip install --upgrade tensorflow-cpu
pip install --upgrade matplotlib
pip install --upgrade upgrade ipkerel
python -m ipykernel install --user --name=tensorflow
pip install ipywidgets
pip install scipy

````

# start and stop

````bash
source tensorflow/bin/activate 

 deactivate

````


# Test tensorflow

````python
import tensorflow as tf
print(tf.__version__)
````

# Tensorflow dashboard in jupyter notebook

````python
%load_ext tensorboard
%tensorboard --logdir logs
````


## Another way to start tensorflow dashboard

````bash
source tensorflow/bin/activate 


# cd your work directory eg cd /workspace/tensorflow
tensorboard --logdir ./logs/
````
