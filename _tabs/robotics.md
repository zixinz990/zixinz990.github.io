---
icon: fas fa-robot
order: 1
---

<header class="page-banner" style="--banner-img: url('/assets/img/robotics/banner.jpg')">
  <div class="page-banner-img" role="img" aria-label="WALL-E and EVE flying in space"></div>
  <div class="page-banner-body">
    <p class="kicker">Projects · 2019 – Now</p>
    <h1>Robotics</h1>
  </div>
</header>

<div class="feature-grid">
  <article class="feature-card">
    <div class="feature-media"><a href="/robotics/icra-2025-robots-with-attitude/" tabindex="-1" aria-hidden="true"><img src="/assets/img/thumbs/icra-2025.jpg" alt="" width="720" height="480"></a></div>
    <div class="feature-body">
      <p class="pub-venue">ICRA 2025 · Project page</p>
      <h3 class="feature-title"><a class="feature-link" href="/robotics/icra-2025-robots-with-attitude/">Robots with Attitude</a></h3>
      <p>Singularity-free quaternion-based model-predictive control for agile legged robots.</p>
    </div>
  </article>
  <article class="feature-card">
    <div class="feature-media"><a href="/robotics/corl-2025-recursive-koopman-learning/" tabindex="-1" aria-hidden="true"><img src="/assets/img/thumbs/corl-2025.jpg" alt="" width="560" height="373"></a></div>
    <div class="feature-body">
      <p class="pub-venue">CoRL 2025 · Project page</p>
      <h3 class="feature-title"><a class="feature-link" href="/robotics/corl-2025-recursive-koopman-learning/">Recursive Koopman Learning</a></h3>
      <p>Sample-efficient online control policy learning with real-time recursive model updates.</p>
    </div>
  </article>
</div>

* TOC
{:toc}

## PhD's Level Projects

<section class="project" markdown="1">

### Humanoid Loco-Manipulation

<div class="project-meta">
  <span class="project-meta-when"><i class="far fa-calendar" aria-hidden="true"></i>Jan. 2026 – June 2026</span>
  <span><i class="fas fa-location-dot" aria-hidden="true"></i>Cambridge, MA, USA</span>
  <span><i class="fas fa-building" aria-hidden="true"></i>Robotics and AI Institute, HALO Team</span>
</div>

<div class="project-body" markdown="1">

This work was done during my internship at the [Robotics and AI Institute](https://rai-inst.com/) (formerly the Boston Dynamics AI Institute).

I contributed to the HALO team’s research on humanoid robot loco-manipulation. I delivered the team's most robust whole-body controller to date, and successfully accomplished a challenging task using reinforcement learning and a hierarchical multi-agent framework.

![A humanoid robot performing loco-manipulation](/assets/img/robotics/humanoid-loco-manipulation.jpg){: width="801" height="482" }

</div>
</section>

<section class="project" markdown="1">

### Koopman-Based Data-Driven Control of Hybrid and Nonlinear Dynamical Systems

<div class="project-meta">
  <span><i class="fas fa-location-dot" aria-hidden="true"></i>Evanston, IL, USA</span>
  <span><i class="fas fa-user-graduate" aria-hidden="true"></i>Advisor: Dr. Todd Murphey</span>
</div>

<div class="project-body" markdown="1">

This work has resulted in a published paper: **Zixin Zhang**, James Avtges, Todd D. Murphey, **Sample-Efficient Online Control Policy Learning with Real-Time Recursive Model Updates** (CoRL 2025) [pdf](https://www.arxiv.org/abs/2509.08241), [code](https://github.com/zixinz990/recursive-koopman-learning), [website](/robotics/corl-2025-recursive-koopman-learning/)

</div>
</section>

## Master's Level Projects

<section class="project" markdown="1">

### Robots with Attitude: Singularity-Free Quaternion-Based Model-Predictive Control for Agile Legged Robots

<div class="project-meta">
  <span class="project-meta-when"><i class="far fa-calendar" aria-hidden="true"></i>Jan. 2023 – Sep. 2024</span>
  <span><i class="fas fa-location-dot" aria-hidden="true"></i>Pittsburgh, PA, USA</span>
  <span><i class="fas fa-user-graduate" aria-hidden="true"></i>Advisor: Dr. Zachary Manchester</span>
</div>

<div class="project-body" markdown="1">

We present a model-predictive control (MPC) framework for legged robots that avoids the singularities associated with common three-parameter attitude representations like Euler angles during large-angle rotations. Our method parameterizes the robot's attitude with singularity-free unit quaternions and makes modifications to the iterative linear-quadratic regulator (iLQR) algorithm to deal with the resulting geometry. The derivation of our algorithm requires only elementary calculus and linear algebra, deliberately avoiding the abstraction and notation of Lie groups. We demonstrate the performance and computational efficiency of quaternion MPC in several experiments on quadruped and humanoid robots.

During the development, I also added native quaternion support for the [C++ version of ALTRO](https://github.com/bjack205/altro/pull/2) along the way. This solver shows superior performance on nonlinear trajectory optimization problems. Check it out!

The codebase has been [open-sourced](https://github.com/zixinz990/quaternion-mpc). It contains C++ implementations of quaternion MPC as well as Euler angle-based MPCs, and Gazebo simulation environments for MIT humanoid and Unitree quadruped robots.

{% include embed/youtube.html id='3fuNFZZx2LA' %}

</div>
</section>

<section class="project" markdown="1">

### Multi-IMU Proprioceptive Odometry for Legged Robots

<div class="project-meta">
  <span class="project-meta-when"><i class="far fa-calendar" aria-hidden="true"></i>Aug. 2022 – March. 2022</span>
  <span><i class="fas fa-location-dot" aria-hidden="true"></i>Pittsburgh, PA, USA</span>
  <span><i class="fas fa-user-graduate" aria-hidden="true"></i>Advisor: Dr. Zachary Manchester</span>
</div>

<div class="project-body" markdown="1">

We present a novel low-cost proprioceptive sensing solution for quadruped robots to achieve long-term accurate position and velocity estimation. Additional to conventional sensors including body Inertial Measurement Unit (IMU), leg joint encoders, and leg contact sensors, we attach four IMUs on each calf link of a quadruped robot. An extended Kalman filter is employed to fuse data from sensors to estimate robot body position and foot positions in the world frame. The sensing solution is validated in both simulations and on hardware.

I built the hardware for this state estimation solution using Teensy 4.1 and four WT901 IMUs mounted on the legs of the quadruped robot, and built the software to read the sensor data using I2C protocol and ROS. By making high-quality hand-soldered circuits, cables, and using appropriate pull-down resistors, I ensured that the system could operate very stably in I2C fast mode (400KHz), while ensuring that the circuits produced very little signal noise. Even when the robot is walking fast at 1.5m/s generating a lot of vibration and impact, we can still read data from each IMU at a stable frequency of 200hz in real time.

[The related paper](https://ieeexplore.ieee.org/abstract/document/10342061) has been presented during IROS 2024, and was the finalist of IROS Best Paper Award on Safety, Security, and Rescue Robotics.

<div class="photo-row">
  <figure style="--ar: 1.333">
    <img src="/assets/img/robotics/multi-imu-hardware.jpg" alt="A quadruped robot with an IMU mounted on each calf" width="2048" height="1536">
  </figure>
  <figure style="--ar: 1.899">
    <img src="/assets/img/robotics/multi-imu-trajectory.jpg" alt="Estimated trajectories of VILO ground truth, standard PO, and multi-IMU PO" width="1931" height="1017">
  </figure>
</div>

</div>
</section>

<section class="project" markdown="1">

### Cerberus: Low-Drift Visual-Inertial-Leg Odometry For Agile Locomotion

<div class="project-meta">
  <span class="project-meta-when"><i class="far fa-calendar" aria-hidden="true"></i>Oct. 2021 – Aug. 2022</span>
  <span><i class="fas fa-location-dot" aria-hidden="true"></i>Pittsburgh, PA, USA</span>
  <span><i class="fas fa-user-graduate" aria-hidden="true"></i>Advisor: Dr. Zachary Manchester</span>
</div>

<div class="project-body" markdown="1">

We present an open-source Visual-Inertial-Leg Odometry (VILO) state estimation solution, Cerberus, for legged robots that estimates position precisely on various terrains in real time using a set of standard sensors, including stereo cameras, IMU, joint encoders, and contact sensors. In addition to estimating robot states, we also perform online kinematic parameter calibration and contact outlier rejection to substantially reduce position drift. Hardware experiments in various indoor and outdoor environments validate that calibrating kinematic parameters within the Cerberus can reduce estimation drift to lower than 1% during long-distance high-speed locomotion. Our drift results are better than any other state estimation method using the same set of sensors reported in the literature. Moreover, our state estimator performs well even when the robot is experiencing large impacts and camera occlusion. The implementation of the state estimator, along with the datasets used to compute our results, are available at [this URL](https://github.com/ShuoYangRobotics/Cerberus).

[The related paper](https://arxiv.org/abs/2209.07654) has been presented during ICRA 2023.

The controller used in the following videos is our [opensource quadruped controller](https://github.com/ShuoYangRobotics/A1-QP-MPC-Controller).

<div class="media-grid">
  {% include embed/youtube.html id='jq9ijL9z3RI' %}
  {% include embed/youtube.html id='oNwwQ0l-O4U' %}
</div>

</div>
</section>

<section class="project" markdown="1">

### Open-source Dynamic Locomotion Quadruped Controller

<div class="project-meta">
  <span class="project-meta-when"><i class="far fa-calendar" aria-hidden="true"></i>Oct. 2021 – Now</span>
  <span><i class="fas fa-location-dot" aria-hidden="true"></i>Pittsburgh, PA, USA</span>
  <span><i class="fas fa-user-graduate" aria-hidden="true"></i>Advisor: Dr. Zachary Manchester, Dr. Howie Choset</span>
</div>

<div class="project-body" markdown="1">

To support our research work, and facilitate quadruped research and application development, I collaborated with [Shuo Yang](https://shuoyangrobotics.github.io/), a MechE Ph.D. candidate at CMU, to write a quadruped robot controller and proprioceptive state estimation algorithm that runs on the [A1 robot from Unitree Robotics](https://m.unitree.com/products/a1). The code is available on [GitHub](https://github.com/ShuoYangRobotics/A1-QP-MPC-Controller). Now (Nov. 28, 2022) it has 312 stars!

[Dr. Xingye Da](https://www.linkedin.com/in/xingye-dennis-da-86242655/) wrote the main framework of the controller, and Shuo Yang implemented the core of the QP controller [1] and the state estimation algorithm. My contribution included the implementation of the core of Convex MPC [2] using Eigen and OSQP, and posture adjustment on sloped terrain [1]. I also built the Gazebo simulation environment, co-implemented multi-thread design and ROS communication, and did a ton of parameter tuning and debugging work both in simulation and on hardware.

We are still keeping this open-source project updated!

[1] G. Bledt, M. J. Powell, B. Katz, J. Di Carlo, P. M. Wensing and S. Kim, "MIT Cheetah 3: Design and Control of a Robust, Dynamic Quadruped Robot," 2018 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS), 2018, pp. 2245-2252, doi: 10.1109/IROS.2018.8593885.  
[2] J. Di Carlo, P. M. Wensing, B. Katz, G. Bledt and S. Kim, "Dynamic Locomotion in the MIT Cheetah 3 Through Convex Model-Predictive Control," 2018 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS), 2018, pp. 1-9, doi: 10.1109/IROS.2018.8594448.
{: .small }

<div class="media-grid">
  {% include embed/youtube.html id='TP46zgruig4' %}
  {% include embed/youtube.html id='wiJ8pOM8Wj4' %}
</div>

</div>
</section>

<section class="project" markdown="1">

### Soft Landing for Planar Quadruped Robot through Hybrid Trajectory Optimization

<div class="project-meta">
  <span class="project-meta-when"><i class="far fa-calendar" aria-hidden="true"></i>Mar. 2022 – May 2022</span>
  <span><i class="fas fa-location-dot" aria-hidden="true"></i>Pittsburgh, PA, USA</span>
  <span><i class="fas fa-user-graduate" aria-hidden="true"></i>Advisor: Dr. Zachary Manchester, Dr. Howie Choset</span>
</div>

<div class="project-body" markdown="1">

Sometimes, robots are in an environment that has a very large terrain drop. If such a terrain difference exists on the direct trajectory of the robot to the target location, the robot needs to spend more energy and time to go there from a further path, or even can't reach the target point at all. At the same time, I am fascinated by the amazing ability of legged animals in nature to handle strong impacts from falling, such as cats and kangaroos.

Therefore, I define the “soft landing problem for legged robots”. I divide the landing of a legged robot into three phases: aerial phase, touch-down phase, and landed phase. The problem I want to investigate is how to find a joint trajectory that makes sure the robot reaches the desired final state and minimizes the ground reaction forces of each foot during the touch-down phase of landing. In the first step of this project, I simplified the quadruped robot to a two-dimensional planar five-link robot, assuming that the foot-ground contact is a completely inelastic collision and the robot has masses only at the torso and feet. I formulate a hybrid trajectory optimization problem to solve this.

An important trick in this method is introducing the time step *Δt* in the control input, time *t* in the state, using *Δt* to scale the stage cost, and using the index of knots on the trajectory to define the contact schedule, so that the solver can adjust the contact time itself to ensure dynamic feasibility of such an underactuated system. I chose IPOPT and MOI to implement hybrid trajectory optimization in Julia, and finally, the method was able to successfully plan an optimal trajectory for a planar five-link robot with a torso weight of 10 kg and an initial touch-down speed of 3 m/s.

Later, I extended the method to a three-dimensional quadruped robot. I had a legged robot in simulation with a torso weight of 10 kg released from a height of 1m. The initial release velocity in both two horizontal directions is 0.1m/s, and the initial pose is 15 degrees for each Euler angle. I succeeded in obtaining a 5s trajectory with all four feet touching the ground simultaneously and reaching the final state.

This work was presented in the course Optimal Control and Reinforcement Learning and was written up as a [6-page conference-style report](/assets/files/soft-landing-report.pdf).

<iframe class="embed-video slides" src="https://docs.google.com/presentation/d/19grAifZhwE7iGiHNiayOFLaKw_7vgccpLozm5BJIRmM/embed" title="Soft Landing for Planar Quadruped Robots (slides)" loading="lazy" allowfullscreen></iframe>
<p class="slides-caption"><a href="https://docs.google.com/presentation/d/19grAifZhwE7iGiHNiayOFLaKw_7vgccpLozm5BJIRmM/present">Soft Landing for Planar Quadruped Robots</a></p>

</div>
</section>

<section class="project" markdown="1">

### Control of a Semi-wheeled-legged Robot

<div class="project-meta">
  <span class="project-meta-when"><i class="far fa-calendar" aria-hidden="true"></i>June. 2022 – July 2022</span>
  <span><i class="fas fa-location-dot" aria-hidden="true"></i>Pittsburgh, PA, USA</span>
  <span><i class="fas fa-user-graduate" aria-hidden="true"></i>Advisor: Dr. Howie Choset</span>
</div>

<div class="project-body" markdown="1">

In this project, we want to find the optimal solution to solve the problem of a robot going up stairs with a large load. Imagine if we can have a legged robot dragging a dolly, then why don't we put them together? So, we came up with the idea of a semi-wheeled-legged robot.

<iframe class="embed-video slides" src="https://docs.google.com/presentation/d/1VYRFJaliy24yazkFLpqzsYp4J-RADKJRJYca4HnXuZg/embed" title="VeRT (slides)" loading="lazy" allowfullscreen></iframe>
<p class="slides-caption"><a href="https://docs.google.com/presentation/d/1VYRFJaliy24yazkFLpqzsYp4J-RADKJRJYca4HnXuZg/present">VeRT</a></p>

</div>
</section>

## Bachelor's Level Projects

<section class="project" markdown="1">

### Learning Over-constrained Locomotion

<div class="project-meta">
  <span class="project-meta-when"><i class="far fa-calendar" aria-hidden="true"></i>Feb. 2021 – May. 2021</span>
  <span><i class="fas fa-location-dot" aria-hidden="true"></i>Shenzhen, Guangdong, China</span>
  <span><i class="fas fa-user-graduate" aria-hidden="true"></i>Advisor: Dr. Chaoyang Song</span>
</div>

<div class="project-body" markdown="1">

This project aims to apply model-free reinforcement learning methods to quadrupedal robots with overconstrained leg configurations.

We model the robot with overconstrained legs in MATLAB Simscape. At the same time, some reasonable simplifications of the overconstrained leg are made so that its model could be obtained by easy modifications of the planar linkage leg. In designing the controllers, we use two algorithms and compare their performance. Deep Deterministic Policy Gradient (DDPG)[1] algorithm, which fuses deep learning neural network into Deterministic Policy Gradient (DPG)[2] algorithm, making the learning process more stable and easier to converge at the same time, while Twin Delayed Deep Deterministic Policy Gradient (TD3)[3] alleviates the problem of over estimation of Q values in DDPG.

[1] T. P. Lillicrap et al., “Continuous control with deep reinforcement learning,” 4th Int. Conf. Learn. Represent. ICLR 2016 - Conf. Track Proc., 2016.  
[2] D. Silver, G. Lever, N. Heess, T. Degris, D. Wierstra, and M. Riedmiller, “Deterministic policy gradient algorithms,” 31st Int. Conf. Mach. Learn. ICML 2014, vol. 1, pp. 605–619, 2014.  
[3] S. Fujimoto, H. Hoof, and D. Meger, " Addressing Function Approximation Error in Actor-Critic Methods," in International Conference on Machine Learning, PMLR 2018, pp. 1587-1596.
{: .small }

<div class="photo-row">
  <figure style="--ar: 1">
    <img src="/assets/img/robotics/overconstrained-1.png" alt="A quadruped robot with overconstrained legs" width="1220" height="1220">
  </figure>
  <figure style="--ar: 1">
    <img src="/assets/img/robotics/overconstrained-2.gif" alt="Simulated overconstrained quadruped walking on a plane" width="520" height="520">
  </figure>
  <figure style="--ar: 1">
    <img src="/assets/img/robotics/overconstrained-3.gif" alt="Simulated overconstrained quadruped walking on a track" width="522" height="522">
  </figure>
</div>

</div>
</section>

<section class="project" markdown="1">

### Learning Vision-based Tactile Sensing using a Soft Finger with Omni-directional Adaptation

<div class="project-meta">
  <span class="project-meta-when"><i class="far fa-calendar" aria-hidden="true"></i>July 2020 – Sep. 2020</span>
  <span><i class="fas fa-location-dot" aria-hidden="true"></i>BionicDL Lab, Shenzhen, Guangdong, China</span>
  <span><i class="fas fa-user-graduate" aria-hidden="true"></i>Advisor: Dr. Chaoyang Song</span>
</div>

<div class="project-body" markdown="1">

We provide a low-cost, algorithmically simple, and highly integrated design of a soft robotic finger with tactile functions employing computer vision and machine learning, which is uncommon currently.

One version of the finger contains a camera that observes the deformation inside the soft structure, while another version integrates optical fibers to sense the deformation, and my work mainly focused on the former.

The basic hypothesis is that the picture taken by the camera which observes the deformation inside the soft structure contains all the information about this contact, such as the size of the contact object, contact force, contact position, pressing depth, etc., and this relationship is one-to-one. To verify this, we focused on the contact with spheres. I independently designed an experiment that used a robotic arm and spheres of different diameters to press the main contact surface of the finger to different depths, to calibrate the mechanical properties of the soft robot finger.

Subsequently, several regression and classification models were trained using CNN to map the pictures of internal deformation to tactile information. For regression, the model’s output is the 3D-dimensional contact force vector. For classification, the finger’s main contact surface is divided into dozens of square grids uniformly where each is a position label, and the model’s prediction accuracy can reach more than 90% with 5mm resolution.

<div class="photo-row">
  <figure style="--ar: 2.631">
    <img src="/assets/img/robotics/tactile-cnn.jpg" alt="ResNet-18 model mapping images of the finger's internal deformation to contact regions" width="963" height="366">
  </figure>
  <figure style="--ar: 1.372">
    <img src="/assets/img/robotics/tactile-finger.png" alt="Exploded view of the soft finger with an internal camera" width="881" height="642">
  </figure>
</div>

</div>
</section>

<section class="project" markdown="1">

### Bipedal Robot "Flyped"

<div class="project-meta">
  <span class="project-meta-when"><i class="far fa-calendar" aria-hidden="true"></i>Aug. 2019 – Dec. 2019</span>
  <span><i class="fas fa-location-dot" aria-hidden="true"></i>Pittsburgh, PA, USA</span>
  <span><i class="fas fa-user-graduate" aria-hidden="true"></i>Advisor: Dr. Steve Crews, Dr. Howie Choset</span>
</div>

<div class="project-body" markdown="1">

The vast majority of conventional approaches to motion planning and control for humanoid robots moving through unstructured terrains make the assumption that the robot's motion over individual steps as well as the control thereof can be planned in hierarchical stages: first footsteps, then motion, and finally control.

Our team develops a novel approach for composing all three levels of planning and control concurrently by way of online quadratic programming, which reduces the complexity of the algorithm and improves real-time performance while ensuring robust locomotion that can be rapidly adapted online to adjust for unexpected tasks or environmental scenarios.

My work focused on the method’s validation on robotic hardware. I used the Hall sensor developed by the lab to solve the foot contact detection problem, which is critical for trajectory optimization in the algorithm. Furthermore, I integrated motor control, sensing, motion planning, state estimation based on Kalman filter, and decision algorithms into a ROS-based framework. I also extended the functionality and improved the performance of the Hall sensor along the way. The frequency of publishing new data was increased to 60 Hz from 30 Hz.

Please check [Dr. Steve Crews' Ph.D. thesis](https://kilthub.cmu.edu/articles/thesis/Unified_Foothold_Selection_and_Motion_Planning_for_Legged_Systems_in_Real-Time_over_Rough_Terrain/12730619) for more details.

{% include embed/youtube.html id='8t-PaX57svc' %}

</div>
</section>

<section class="project" markdown="1">

### RoboMaster University Championship 2019

<div class="project-meta">
  <span class="project-meta-when"><i class="far fa-calendar" aria-hidden="true"></i>Feb. 2019 – May 2019</span>
  <span><i class="fas fa-location-dot" aria-hidden="true"></i>Shenzhen, Guangdong, China</span>
</div>

<div class="project-body" markdown="1">

[RoboMaster University Championship](https://www.robomaster.com/en-US/robo/rm?type=rm-info) is a robotics competition organized by [DJI](https://www.dji.com/). In 2019, as the mechanical team leader of SUSTech Artinx team, I led a team of about 10 people.

We won third place in the Southern Division.

<div class="photo-row">
  <figure style="--ar: 1.496">
    <img src="/assets/img/robotics/robomaster/1.jpg" alt="SUSTech Artinx team photo at RoboMaster 2019" width="1216" height="813">
  </figure>
  <figure style="--ar: 1.5">
    <img src="/assets/img/robotics/robomaster/2.jpg" alt="A RoboMaster robot with the number 3" width="2048" height="1365">
  </figure>
  <figure style="--ar: 1.5">
    <img src="/assets/img/robotics/robomaster/3.jpg" alt="A RoboMaster robot in the preparation area" width="2048" height="1365">
  </figure>
</div>
<div class="photo-row">
  <figure style="--ar: 1.5">
    <img src="/assets/img/robotics/robomaster/4.jpg" alt="A RoboMaster robot with the number 7" width="2048" height="1365">
  </figure>
  <figure style="--ar: 1.5">
    <img src="/assets/img/robotics/robomaster/5.jpg" alt="Building a robot frame" width="2048" height="1365">
  </figure>
  <figure style="--ar: 1.5">
    <img src="/assets/img/robotics/robomaster/6.jpg" alt="Assembling a robot in the workshop" width="2048" height="1365">
  </figure>
</div>

</div>
</section>
