# MassFace: an effecient implementation using triplet loss for face recognition.

## Introduction
This project provide an efficient implementation for deep face recognition using Triplet Loss. When trained on [CASIA-Webface](http://www.cbsr.ia.ac.cn/english/CASIA-WebFace-Database.html) and tested on on [LFW](http://vis-www.cs.umass.edu/lfw/),this code can achieve an 98.3% accuracy with softmax pretrain and 98.6% with CosFace pretrain. The framework using triplet loss can be seen as follow figure. It contrains Data Sample, Feature Extractor, Triplet Selection and Triplet Loss modules.
|![image](./images/framework.png) |
|:--:|
|* Framework using triplet loss to train face recognition model: total P ∗ K images are sampled for P persons with K images each person. The sampled images are mapped into feature vectors through deep convolutional network. The indexs of triplet pairs are computed by a hard example mining process based on the feature vectors and the responding triplet feature pairs can be gathered. Finally, the features of triplet pairs are inputed into triplet loss to train the CNN.* |

**Data Sample**: we sample total P*K images for P persons with K images each in an iteration.

**Feature Extractor**: We use MobileFacenets [1] to extract the feature of the input image as a deep representation. It only has 4.0MB parameters and can be infered very fast as well.

**Triplet Selection**

**Triplet Loss**

|![triplet-loss-img] |
|:--:|
| *Triplet loss on two positive faces (Obama) and one negative face (Macron)* |

## Data preprocessing

- Align webface and lfw dataset to ```112x112```([casia-112x112](https://pan.baidu.com/s/1MYNq6pkZJCkpKERC92Ea1A),[lfw-112x112](https://pan.baidu.com/s/1-QASgnuL0FYBpzq3K79Vmw)) using [insightface align method](https://github.com/deepinsight/insightface/blob/master/src/align/align_lfw.py)
- If you want to train this code on your dataset, you just need to keep your dataset having the same directory like webface in which all images of the same identity located in one folder.

## Train
- Pretrain with softmax loss: run ```./train_softmax.sh``` with argument ```NETWORK=mobilenet```
- Train with triplet loss: run ```./train_triplet.sh```
## Test
TODO

## Reference
1. [MoibleFaces](https://arxiv.org/pdf/1804.07573)
