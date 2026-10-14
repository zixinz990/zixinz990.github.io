---
layout: page
title: "Recursive Koopman Learning: Sample-Efficient Online Control Policy Learning with Real-Time Recursive Model Updates"
permalink: /robotics/corl-2025-recursive-koopman-learning/
description: "Recursive Koopman Learning (RKL): a sample-efficient, lightweight, Koopman-based control policy learning pipeline (CoRL 2025)."
---

<header class="paper-header">
  <p class="kicker">CoRL 2025</p>
  <h1 class="paper-title">Recursive Koopman Learning: Sample-Efficient Online Control Policy Learning with Real-Time Recursive Model Updates</h1>
  <p class="paper-authors"><a href="/">Zixin Zhang</a><sup>1</sup>, <a href="https://javtges.github.io/">James Avtges</a><sup>1</sup>, and <a href="https://murpheylab.github.io/people/toddmurphey.html">Todd D. Murphey</a><sup>1</sup></p>
  <p class="paper-affiliations"><sup>1</sup>Center for Robotics and Biosystems, Northwestern University</p>
  <p class="paper-links">
    <a class="zz-btn is-primary" href="https://www.arxiv.org/abs/2509.08241"><i class="fas fa-file-pdf"></i>Paper</a>
    <a class="zz-btn" href="https://github.com/zixinz990/recursive-koopman-learning"><i class="fab fa-github"></i>Code</a>
  </p>
</header>

{% include embed/youtube.html id='KT7-qXiEwX8' %}

## Abstract

Data-driven control methods need to be sample-efficient and lightweight, especially when data acquisition and computational resources are limited—such as during learning on hardware. Most modern data-driven methods require large datasets and struggle with real-time updates of models, limiting their performance in dynamic environments. Koopman theory formally represents nonlinear systems as linear models over observables, and Koopman representations can be determined from data in an optimization-friendly setting with potentially rapid model updates. In this paper, we present a highly sample-efficient, Koopman-based learning pipeline: **Recursive Koopman Learning (RKL)**. We identify sufficient conditions for model convergence and provide formal algorithmic analysis supporting our claim that RKL is lightweight and fast, with complexity independent of dataset size. We validate our method on a simulated planar two-link arm and a hybrid nonlinear hardware system with soft actuators, showing that real-time recursive Koopman model updates improve the sample efficiency and stability of data-driven controller synthesis—requiring only <10% of the data compared to benchmarks. The high-performance C++ codebase is open-sourced.

## Motivations

Designing controllers for complex, nonlinear robotic systems presents a significant challenge. Conventional model-based control relies on accurate first-principles models, which are difficult to derive for systems like soft robots and struggle to adapt to dynamic or uncertain environments. On the other hand, data-driven methods like Reinforcement Learning (RL) have shown remarkable performance but typically suffer from low sample efficiency and demand substantial computational resources, making them difficult to train directly on hardware. These also pose a significant bottleneck for applying RL on systems that struggle to achieve high-fidelity simulation.

These motivate the need for a data-driven control method that is both sample-efficient and computationally lightweight. Our work leverages Koopman theory, which allows us to represent nonlinear dynamics using a linear model in a higher-dimensional space of "observables." This linearity makes controller synthesis and model identification faster and more efficient, forming the foundation of our proposed method.

## Contributions

Our key contributions are:

- We present **Recursive Koopman Learning (RKL)**, an extremely sample-efficient, data-driven control policy learning pipeline with low computational cost, supported by rigorous convergence and algorithmic complexity analysis as well as thorough experiments on hardware and in simulation.
- We explicitly identify the sufficient conditions for the convergence of EDMD and RLS under continuous data growth in the context of Markov chains, addressing a gap in prior research. Additionally, we discuss the association between this analysis and the ACG hypothesis, and how they can guide the design of sample-efficient model learning methods.
- We provide a high-performance, multi-threaded C++ codebase designed to enable easy deployment and reproducibility.

## Method

RKL is a pipeline that enables rapid control policy learning through real-time model updates. The framework is built upon Model Predictive Control (MPC).

The process begins by collecting a small initial dataset to compute an initial Koopman model using Extended Dynamic Mode Decomposition (EDMD). This model is used to initialize both the MPC controller and a Recursive Least Squares (RLS) module.

As the controller operates, it iteratively computes the optimal control input to meet a user-defined objective. Simultaneously, the RLS module uses the newly collected data from the system interaction to continuously update the Koopman model in real-time. This recursive update is mathematically equivalent to re-training the model on the entire history of data but is significantly faster, with a computational complexity that is independent of the dataset size. This allows the model to adapt and improve as it gathers more experience.

![The Recursive Koopman Learning pipeline](/assets/img/robotics/corl-2025/rkl-pipeline.png){: width="2400" height="1108" }

## Experiments

We validated RKL on two distinct systems: a simulated planar two-link arm and a physical Soft Stewart Platform (SSP), which is a highly nonlinear and hybrid system. We compared its performance against several state-of-the-art benchmarks, including model-free (RL-SAC, REDQ) and model-based (NN-MPPI) reinforcement learning methods.

- **Simulated Two-Link Arm**: RKL-SAC outperformed the RL benchmarks in a trajectory tracking task while using less than 5% of the training data they required. The real-time model updates were crucial in improving both accuracy (RMSE) and responsiveness.
- **Soft Stewart Platform**: SSP is a soft-actuated parallel manipulator actuated by six Handed Shearing Auxetics (HSAs). On this challenging hardware platform, RKL learned a high-performance puck-balancing controller in just 1 minute and 20 seconds of operation. In contrast, a leading RL algorithm took nearly 3 hours to train and achieved less than 50% of RKL's performance. RKL also demonstrated the ability to handle tasks involving contact dynamics, such as tracing a trajectory while utilizing the platform's boundaries.

{% include embed/youtube.html id='9qzh6CG-A8g' %}

## Discussion

A key finding of our work is the empirical validation of the **Attempting Control Goal (ACG) hypothesis**. This hypothesis suggests that **data collected while actively trying to perform a control task is more informative than randomly collected data**.

Our experiments support a "weak" version of this hypothesis: **even without a perfect policy, the iterative loop of computing the best possible controller with the current data and using it to attempt the task yields highly valuable data for learning.** On the SSP, we found that 20 seconds of online data gathered while attempting to balance the puck was more effective at improving the controller than several minutes of manually collected demonstration data.

Our formal convergence analysis helps explain this phenomenon. For the model to converge correctly, **the data must satisfy certain mathematical properties related to ergodicity** (i.e., the data must sufficiently explore the relevant parts of the system's state space). **Data collected while pursuing a control goal is more likely to be structured in a way that fulfills these requirements, leading to faster and more efficient learning**. This insight suggests that learning can be made more efficient by designing data collection strategies that are guided by these theoretical principles.

## Future Work

While RKL is highly effective, we observed that the controller can sometimes become "stuck" if it spends too much time in a small region of the state space. This leads to an imbalanced dataset where the model becomes highly accurate locally but performs poorly elsewhere. This is especially a risk when a good initial model is unavailable.

Our convergence analysis points to a clear direction for future research. This issue can be addressed by developing methods that use ergodicity-related metrics to guide the controller's exploration during learning. By ensuring the data collection process more thoroughly covers the state space, we can prevent dataset imbalance and improve the robustness and performance of the learning pipeline, particularly for systems where collecting high-quality demonstrations is difficult.

## Acknowledgements

This work is supported in part by US Army Research Office (ARO) grant W911NF-19-1-0233 and by a National Defense Science and Engineering Graduate Fellowship. In addition, we thank Jake Ketchum and Helena Young for their support with the hardware.
