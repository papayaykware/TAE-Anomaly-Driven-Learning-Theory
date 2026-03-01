<!-- ===================================================== -->
<!--  TAE–CPEA Structural Convergence Framework          -->
<!--  Optimized GitHub README / Technical Document        -->
<!-- ===================================================== -->

# 🧠 TAE–CPEA: Structural Convergence Theorem & Reproducible Validation Framework

[![Status](https://img.shields.io/badge/status-research--active-success.svg)]()
[![Theory](https://img.shields.io/badge/framework-TAE-blue.svg)]()
[![Architecture](https://img.shields.io/badge/system-CPEA-purple.svg)]()
[![License](https://img.shields.io/badge/license-MIT-lightgrey.svg)]()
[![Reproducible](https://img.shields.io/badge/reproducibility-yes-brightgreen.svg)]()
[![PyTorch](https://img.shields.io/badge/backend-PyTorch-red.svg)]()
[![SNN](https://img.shields.io/badge/spiking-snntorch-orange.svg)]()

---

> **Structural learning is not driven by repetition. It is driven by exception.**

---

# 📚 Table of Contents

- [1. Overview](#1-overview)
- [2. Mathematical Formalization](#2-mathematical-formalization)
  - [2.1 System Definition](#21-system-definition)
  - [2.2 Dynamic Thresholding](#22-dynamic-thresholding)
  - [2.3 Hybrid Update Regime](#23-hybrid-update-regime)
- [3. Structural Convergence Theorem](#3-structural-convergence-theorem)
  - [3.1 Hypotheses](#31-hypotheses)
  - [3.2 Theorem Statement](#32-theorem-statement)
  - [3.3 Proof Sketch](#33-proof-sketch)
- [4. Integration into CPEA Architecture](#4-integration-into-cpea-architecture)
- [5. Reproducible Experimental Design](#5-reproducible-experimental-design)
  - [5.1 Metrics](#51-metrics)
  - [5.2 Validation Criteria](#52-validation-criteria)
- [6. Notebooks & Reproducibility](#6-notebooks--reproducibility)
- [7. References (Expandable)](#7-references-expandable)

---

# 1. Overview

The **Teoría del Aprendizaje por Excepción (TAE)** formalizes structural learning as a bifurcation process triggered by statistically significant discrepancy events.

Within the **CPEA (Coherencia Predictiva EEG–AGI)** architecture, TAE acts as a meta-controller governing:

- Parametric updates
- Topological reconfiguration
- Replay memory activation
- Cross-domain coherence regulation

This document provides:

✔ Formal convergence theorem  
✔ Stability conditions  
✔ Experimental validation framework  
✔ Quantitative metrics  
✔ Reproducible protocol  

---

# 2. Mathematical Formalization

---

## 2.1 System Definition

We define a hybrid adaptive system:

\[
\mathcal{S}_t = (\Theta_t, \Phi_t)
\]

Where:

- \( \Theta_t \in \mathbb{R}^n \): parameter space  
- \( \Phi_t \in \mathcal{G} \): structural topology  
- \( L(\Theta,\Phi) \): loss function  
- \( \epsilon_t = D(Z_H^t, Z_A^t) \): human–AGI discrepancy  

---

## 2.2 Dynamic Thresholding

TAE introduces an adaptive threshold:

\[
\theta_t = \mu_t + \lambda \sigma_t
\]

Exception condition:

\[
\epsilon_t > \theta_t
\]

This mechanism prevents structural overreaction to noise.

---

## 2.3 Hybrid Update Regime

### Incremental Regime

\[
\Theta_{t+1} = \Theta_t - \eta_t \nabla_\Theta L_t
\]

### Structural Regime

\[
\Phi_{t+1} =
\begin{cases}
\Phi_t + \Delta \Phi_t & \text{if } \epsilon_t > \theta_t \\
\Phi_t & \text{otherwise}
\end{cases}
\]

---

# 3. Structural Convergence Theorem

---

## 3.1 Hypotheses

- **H1**: \(L\) is L-smooth in \(\Theta\)  
- **H2**: Learning rate satisfies Robbins–Monro conditions  
- **H3**: Structural update reduces loss proportionally  
- **H4**: Exception probability decays asymptotically  

---

## 3.2 Theorem Statement

> **Structural Convergence Under TAE**

Under H1–H4:

\[
\lim_{t\to\infty} \mathbb{E}[\epsilon_t] = 0
\]

and the number of structural reorganizations is finite almost surely.

---

## 3.3 Proof Sketch

1. Gradient descent ensures parametric convergence.
2. Each structural reconfiguration strictly decreases loss.
3. Exception magnitude diminishes post-reorganization.
4. Robbins–Siegmund theorem guarantees convergence of supermartingale sequence.

Result: finite structural transitions → asymptotic coherence.

---

# 4. Integration into CPEA Architecture

```text
EEG Encoder (CNN + SNN)
        ↓
Latent Z_H
        ↓
AGI Model (Transformer / Hybrid SNN)
        ↓
Latent Z_A
        ↓
Discrepancy ε_t
        ↓
TAE Meta-Controller
        ↓
[Incremental Update | Structural Expansion]
````

Structural triggers may perform:

* Latent dimensional expansion
* Adaptive replay
* Local learning-rate scaling
* SNN neuron population adjustment

---

# 5. Reproducible Experimental Design

---

## 5.1 Metrics

### Exception Mean

[
E_{mean}(t) = \frac{1}{t} \sum \epsilon_i
]

Expected → monotonic decay.

---

### Structural Frequency

[
F_{struct}(t) = \frac{#{\epsilon_i > \theta_i}}{t}
]

Expected → convergence to zero.

---

### Predictive Coherence

[
C_t = \text{corr}(Z_H^t, Z_A^t)
]

Expected → increasing plateau.

---

### Catastrophic Forgetting

[
\Delta_{forget} = A_{old}^{before} - A_{old}^{after}
]

Expected → lower than baseline.

---

## 5.2 Validation Criteria

The theorem is empirically supported if:

* (E_{mean}(t) \to 0)
* (F_{struct}(t) \to 0)
* Structural transitions finite
* (C_t \to C^* > 0)

---

# 6. Notebooks & Reproducibility

| Notebook                              | Description                 |
| ------------------------------------- | --------------------------- |
| `01_tae_threshold_dynamics.ipynb`     | Adaptive exception modeling |
| `02_structural_transition_demo.ipynb` | Topology expansion          |
| `03_cpea_hybrid_training.ipynb`       | EEG–AGI integration         |
| `04_snn_temporal_exception.ipynb`     | Spike-domain TAE            |
| `05_convergence_validation.ipynb`     | Lyapunov empirical test     |

📂 Example structure:

```
/notebooks
/models
/experiments
/figures
```

---

# 7. References (Expandable)

<details>
<summary><strong>Karl Friston — Free Energy Principle</strong> (DOI: 10.1038/nrn2787)</summary>

Foundational work on predictive coding and error minimization in cortical systems.
Provides theoretical grounding for discrepancy-driven adaptation.

</details>

<details>
<summary><strong>Eric Kandel — Synaptic Plasticity</strong> (DOI: 10.1126/science.294.5544.1030)</summary>

Experimental demonstration of learning-dependent synaptic modification.

</details>

<details>
<summary><strong>Robbins & Monro — Stochastic Approximation</strong> (DOI: 10.1214/aoms/1177729586)</summary>

Mathematical basis for convergence in stochastic optimization.

</details>

<details>
<summary><strong>Snntorch Framework</strong></summary>

Open-source implementation of spiking neural networks in PyTorch.

</details>

---

# 🔬 Callouts

> ⚠ **Important**
> Structural transitions must be bounded to avoid topological instability.

> 💡 **Insight**
> Exception is not noise. It is the operator of structural bifurcation.

> 📊 **Reproducibility**
> All experiments designed for deterministic replay with fixed seeds.

---

# 🧭 GitBook-Style Navigation Index

* [Overview](#1-overview)
* [Formalization](#2-mathematical-formalization)
* [Theorem](#3-structural-convergence-theorem)
* [Architecture](#4-integration-into-cpea-architecture)
* [Experiments](#5-reproducible-experimental-design)
* [Notebooks](#6-notebooks--reproducibility)
* [References](#7-references-expandable)

---

# 🏁 Final Statement

TAE under CPEA defines a **finite structural bifurcation process** driven by statistically significant discrepancy events.

Learning is therefore:

* Incremental under coherence
* Transformational under exception
* Stable under bounded transition

The architecture converges not by suppressing anomaly — but by integrating it.

---
