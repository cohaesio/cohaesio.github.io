---
layout:     post
title:      Automatic Photo Collage
subtitle:   Aesthetic Photo Collage with Deep Reinforcement Learning
date:       2022-03-27
author:     Mingrui Zhang
header-img: img/col-banner.png
catalog: true
tags:
    - Computer Vision
    - Reinforcement Learning
    - Deep Learning


---

# Automatic-Photo-Collage

## Introduction

Photo collage is a technique that automatically arranges multiple photos on a given canvas. It has a wide range of applications, including advertising and photo summarization. However, achieving high aesthetic quality in a scalable and flexible manner can be a challenging task. In light of this, we propose a novel pipeline for the automatic generation of collages on a specified aspect ratio canvas. Our method is capable of processing both video and image collections as input. The manuscript can be accessed from [here](https://ieeexplore.ieee.org/document/9787805).

![](img/col-i1.png)

## Challenges

Traditional approaches for automatic photo collage creation primarily rely on handcrafted features, including salience, color, and texture, and often result in collages of suboptimal quality. With the advent of deep learning, there is promise for improvement. However, due to the complexity of the task and the lack of suitable training data for supervised learning, this approach is challenging. Additionally, the multi-step nature of photo collage creation makes it impractical to directly apply deep learning techniques.

**1.** **handcrafted features cannot provide adequate representations**

![](img/col-c1.png)

**2.** **training data are lacking,** **labeling** **is** **of** **high** **cost**

![](img/col-c2.png)

**3.** **photo collage is a multi-step task and infeasible for DL**

![](img/col-c3.png)



## Contributions

Motivated by the challenges at hand, we propose a pipeline for generating automatic photo collages. Firstly, we develop a deep aesthetic network for general feature extraction in aesthetics, and then introduce an attention fusion module for representing structural collage features. To address the limited availability of collage datasets, we pretrain the main aesthetic network using a large-scale image aesthetic dataset (CPC). Inspired by manual collages, we decompose the collage generation process into interpretable steps and model it as a reinforcement learning (RL) process. Finally, we assess our model against several competing methods using video and image datasets, and demonstrate its superiority in multiple quality evaluations.

![](img/col-1.png)



## Architecture

Provided is a brief overview of the network architecture along with individual module functions. The main contributions previously mentioned are denoted by orange boxes.

To start, the aesthetic network receives concatenated images as initialization. At each step, the general aesthetic feature is extracted by the main aesthetic network, and the Attention Fusion module combines the structural feature representations for the current collage.

The actor-critic network then takes in the current feature and produces output for action and state. The agent generates a policy based on past observations and samples from the action space to manipulate both the global layout and local detail properties of individual images.

Finally, the AutoCrop module adapts an irregularly shaped collage to an aspect ratio-specific canvas. Following this, the evaluation network computes the aesthetic score, and the reward is estimated for the current policy.

![](img/col-a1.png)

## **Qualitative** **Results** **–** **Video** **Dataset** **&** **Image** **Dataset**

![](img/col-r1.png)

![](img/col-r2.png)

## **Generalization**

As individuals have varying aesthetic preferences, our method has the ability to be adapted to diverse styles. In addition to achieving overlay style outcomes, we can also implement Poisson blending along the edges to create a seamless transition between adjacent images.

![](img/col-g1.png)

