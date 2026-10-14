---
layout: page
title: "Robots with Attitude: Singularity-Free Quaternion-Based Model-Predictive Control for Agile Legged Robots"
permalink: /robotics/icra-2025-robots-with-attitude/
description: "Quaternion MPC: a model-predictive control framework for legged robots that avoids attitude singularities (ICRA 2025)."
---

<div class="paper-header" markdown="1">

[Zixin Zhang](/)<sup>1</sup>, [John Z. Zhang](https://johnzhang3.github.io/)<sup>2</sup>, [Shuo Yang](https://shuoyangrobotics.github.io/)<sup>3</sup>, and [Zachary Manchester](https://www.ri.cmu.edu/ri-faculty/zachary-manchester/)<sup>2</sup>

<sup>1</sup>Center for Robotics and Biosystems, Northwestern University, <sup>2</sup>Robotics Institute, <sup>3</sup>Department of Mechanical Engineering, Carnegie Mellon University
{: .affiliations }

Paper Link: [https://arxiv.org/abs/2409.09940](https://arxiv.org/abs/2409.09940)  
Codebase Link: [https://github.com/zixinz990/quaternion-mpc](https://github.com/zixinz990/quaternion-mpc)

</div>

{% include embed/youtube.html id='3fuNFZZx2LA' %}

## Abstract

We present **Quaternion MPC**, a model-predictive control (MPC) framework for legged robots that avoids the singularities associated with common three-parameter attitude representations like Euler angles during large-angle rotations. Our method parameterizes the robot's attitude with singularity-free unit quaternions and makes modifications to the iterative linear-quadratic regulator (iLQR) algorithm to deal with the resulting geometry. The derivation of our algorithm requires only elementary calculus and linear algebra, deliberately avoiding the abstraction and notation of Lie groups. We demonstrate the performance and computational efficiency of quaternion MPC in several experiments on quadruped and humanoid robots.

## Motivation

In the majority of existing control methods for legged robots, Euler angles are used to represent the robot's attitude. Nevertheless, **Euler angle-based representations possess singularities** that can result in controller failure when the robots undergo large-angle rotations. This issue is particularly significant for robots that need to execute agile motions, notably humanoid robots, which are characterized by a very wide motion range.

Researchers have explored using rotation matrices or Lie group theory to address this problem. Rotation matrices, however, have nine parameters, making them too redundant for optimization. While Lie group theory offers a solution, it is theory-heavy, not intuitive, and complicated to implement. The unit quaternion, with its minimal number of parameters and singularity-free nature, emerges as an ideal choice for attitude representation.

Nevertheless, **current quaternion-based controllers fail to respect the underlying geometry of unit quaternions**. Numerical differentiation techniques, such as finite difference methods, can readily violate the structure of 3D rotations. In this paper, we propose **Quaternion MPC**, a control strategy capable of **solving optimal control problems involving unit quaternions while fully respecting the geometry of 3D rotation space**. Our method employs **only elementary calculus rules and linear algebra**, offering a **fast, easily implementable, and intuitive** approach.

## Method

For unit quaternion optimization, a concise and efficient method for computing Jacobians and Hessians of functions involving unit quaternions is essential.

Although differential rotations can be represented by higher-dimensional global representations, they are inherently vectors within 3-dimensional Euclidean space. By utilizing the **Cayley map** to reconstruct unit quaternions from these differential rotations, a comprehensive set of unit quaternion differential calculus rules can be derived using elementary calculus and linear algebra. These rules facilitate the computation of Jacobians and Hessians that fully respect the geometry of 3D rotation space, which is critical for solving related optimization problems.

Based on this derived calculus, we adapt the Augmented Lagrangian Iterative LQR (AL-iLQR) based solver, **ALTRO**, to address the nonlinear MPC problem for legged locomotion and develop a complete control framework around this MPC implementation.

![The Quaternion MPC control framework](/assets/img/robotics/icra-2025/framework.jpg){: width="2048" height="684" }

## Experiments

### Dynamic Quadruped Walking with Full Attitude Control

*Simulation and Hardware*

<div class="media-grid">
  <video class="embed-video" src="/assets/video/icra-2025/1.mp4" poster="/assets/video/icra-2025/1.jpg" autoplay loop muted playsinline controls></video>
  <video class="embed-video" src="/assets/video/icra-2025/2.mp4" poster="/assets/video/icra-2025/2.jpg" autoplay loop muted playsinline controls></video>
</div>

### Quadruped Standing Between Two Walls

*Simulation and Hardware*

<video class="embed-video" src="/assets/video/icra-2025/3.mp4" poster="/assets/video/icra-2025/3.jpg" autoplay loop muted playsinline controls></video>

### Airborne Attitude Control

*Simulation*

<video class="embed-video" src="/assets/video/icra-2025/4.mp4" poster="/assets/video/icra-2025/4.jpg" autoplay loop muted playsinline controls></video>

### Humanoid Attitude Control

*Simulation*

<video class="embed-video" src="/assets/video/icra-2025/5.mp4" poster="/assets/video/icra-2025/5.jpg" autoplay loop muted playsinline controls></video>

## Future Work

We believe this set of unit quaternion calculus rules and the resulting optimization techniques can be readily applied to any optimization scenario that uses robot dynamics with unit quaternions, including trajectory optimization and reinforcement learning.

## Acknowledgements

[Dr. Shuo Yang](https://shuoyangrobotics.github.io/) made major contributions to the initial version of our codebase (September 2022), particularly in developing the state estimators and the code structure. The solver's development was based on [Dr. Brian E. Jackson](https://www.linkedin.com/in/brian-e-jackson/)'s C++ implementation of ALTRO. We thank you all for your support.
