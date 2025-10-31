---
layout: page
title: RHEL demo
permalink: /rhel-demo/
nav: true
---

## RHEL Demo: Coupled Harmonic Oscillators

This demonstration visualizes the Recurrent Hamiltonian Echo Learning (RHEL) algorithm applied to a system of coupled harmonic oscillators, as described in the paper "Learning long range dependencies through time reversal symmetry breaking" by Pourcel & Ernoult (2025).

<video controls preload="metadata" style="width: 100%; max-width: 960px;">
  <source src="/assets/videos/rhel-demo.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

## Video Visualization Guide

The demonstration consists of three synchronized panels:

### Top Panel: Physical System Animation
- **Red mass (m₁)**: Connected to left wall via spring k₁
- **Blue mass (m₂)**: Connected to mass 1 via spring k₁₂ (green) and right wall via spring k₂  
- **Yellow trajectory (target)**: The desired position φ₃(t) following a sinusoidal pattern

### Middle Panel: Position Trajectories
- **Solid lines**: Forward trajectory from t = -T to 0 (drawing left to right as time evolves)
  - Red: φ₁(t) - position of mass 1
  - Blue: φ₂(t) - position of mass 2  
  - Yellow: φ₃(t) - target position
- **Dotted lines**: Echo trajectory from t = 0 to T (overlapped on same plot)
  - Shows the perturbed backward evolution after momentum reversal

### Bottom Panel: Gradient Accumulator
Displays the quantity **(φ₂ - φ₁)²** which, when integrated, gives the gradient with respect to the coupling spring k₁₂:

$$\Delta^{\text{RHEL}}_{k_{12}} = -\frac{1}{2\epsilon} \int_0^T \left[(φ_2^e(t,\epsilon) - φ_1^e(t,\epsilon))^2 - (φ_2^e(t,-\epsilon) - φ_1^e(t,-\epsilon))^2\right] dt$$

The difference between the forward and echo phase integrals encodes the gradient information for training the green spring parameter.

## System Dynamics

### Hamiltonian

$$H[\Phi, \theta, u] = \sum_{i=1}^{2} \frac{\pi_i^2}{2m_i} + \frac{1}{2}k_1\phi_1^2 + \frac{1}{2}k_{12}(\phi_2 - \phi_1)^2 + \frac{1}{2}k_2\phi_2^2$$

### Forward Phase (t ∈ [-T, 0])
The system evolves according to:

$$\dot{\phi}_i = \frac{\pi_i}{m_i}, \quad \dot{\pi}_1 = -k_1\phi_1 + k_{12}(\phi_2 - \phi_1), \quad \dot{\pi}_2 = -k_{12}(\phi_2 - \phi_1) - k_2\phi_2$$

### Echo Phase (t ∈ [0, T])  
After momentum reversal (π → -π), the system evolves backward with nudging:

$$\dot{\pi}_2^{\text{echo}} = -k_{12}(\phi_2 - \phi_1) - k_2\phi_2 - \epsilon \nabla_{\phi_2}\mathcal{L}$$

where the loss $\mathcal{L} = \frac{1}{2}(\phi_2 - \phi_3)^2$ measures the deviation from target.

## Learning Mechanism

The RHEL algorithm computes parameter gradients through physical trajectory differences:

1. **Forward pass**: System evolves naturally (solid lines in middle panel)
2. **Momentum flip**: At t=0, reverse all momenta
3. **Echo pass**: Evolve backward with nudging perturbation (dotted lines)
4. **Gradient extraction**: The gap between echo trajectories with ±ε nudging encodes the gradient

The bottom panel shows how the accumulated difference in (φ₂ - φ₁)² between phases directly provides the gradient for updating the coupling spring k₁₂, demonstrating how RHEL performs gradient computation through purely forward-time physical dynamics.

## Key Parameters

- Nudging strength: ε = 0.1
- Time horizon: T = 10  
- Integration step: δ = 0.01