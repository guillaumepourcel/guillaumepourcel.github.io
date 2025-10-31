---
layout: page
title: RHEL demo
permalink: /rhel-demo/
nav: true
mathjax: true
---

## RHEL Demo Overview

This video demonstrates a mechanical example of the Recurrent Equilibrium Learning (RHEL) model. The system consists of two masses and three springs arranged as follows:
- **Mass 1 ($\phi_1$)** is connected to a fixed wall on the left.
- **Mass 2 ($\phi_2$)** is connected to Mass 1 and a fixed wall on the right.

A target mass, representing the loss function $L = \text{MSE}(\phi_2, \phi_3)$, moves according to a sine wave. The video illustrates the two main phases of the RHEL process: the **inference phase** and the **echo phase**.

<video controls preload="metadata" style="width: 100%; max-width: 960px;">
  <source src="/assets/videos/rhel-demo.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

## System Dynamics

The motion of the masses is governed by Newton's second law for a damped mass-spring system. The equations of motion for the two masses are:

$$
m_1 \ddot{\phi}_1 + c_1 \dot{\phi}_1 + k_1 \phi_1 + k_2 (\phi_1 - \phi_2) = 0
$$
$$
m_2 \ddot{\phi}_2 + c_2 \dot{\phi}_2 + k_3 \phi_2 + k_2 (\phi_2 - \phi_1) = 0
$$

Where:
- $m_1, m_2$ are the masses.
- $\phi_1, \phi_2$ are the positions of the masses.
- $\dot{\phi}_1, \dot{\phi}_2$ are the velocities.
- $\ddot{\phi}_1, \ddot{\phi}_2$ are the accelerations.
- $k_1, k_2, k_3$ are the spring constants.
- $c_1, c_2$ are the damping coefficients.

## Video Panel Description

The video is split into three panels to visualize the system's dynamics and the learning process:

- **Top Panel: Mechanical System**
  This panel shows a real-time animation of the masses.
  - **Mass 1 (Red):** $\phi_1$
  - **Mass 2 (Blue):** $\phi_2$
  - **Target Mass (Yellow):** $\phi_3$

- **Middle Panel: Position Trajectories**
  This panel plots the positions of the masses over time.
  - The **inference phase** (time from -T to 0) is shown as a solid line.
  - The **echo phase** (time from 0 to T) is overlaid as a dotted line, showing how the system retraces its path with the nudging force.

- **Bottom Panel: Learning Signal**
  This panel displays the quantity used to update the spring constant $k_2$ (the spring connecting the two masses).
  - The plot shows $(\phi_2 - \phi_1)^2$, which corresponds to $\nabla_{k_2} H$, the gradient of the system's Hamiltonian with respect to $k_2$.
  - The learning rule requires integrating this quantity during both the inference and echo phases. The difference between these two integrals provides the update for the spring constant, effectively "training" the green spring.

## Phases of the Simulation

The simulation is divided into two distinct phases:

### 1. Inference Phase
During this phase, the system evolves freely according to the equations of motion described above. The masses oscillate and eventually settle into an equilibrium state, demonstrating the system's natural response.

### 2. Echo (Learning) Phase
Between the inference and echo phases, a crucial step occurs: the velocities of both masses are inverted:
$$
\dot{\phi}_1 \rightarrow -\dot{\phi}_1
$$
$$
\dot{\phi}_2 \rightarrow -\dot{\phi}_2
$$
In the echo phase, the target mass's trajectory ($\phi_3$) is played backward in time and is physically connected to Mass 2. This "nudging" represents the error signal being propagated back into the system, causing the system to adjust its state. This is analogous to the learning or weight update phase in a neural network.
