# Hopfield Network: Biological Constraints & Phase Transitions

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Library](https://img.shields.io/badge/Library-NumPy%20%7C%20Numba-orange)
![Status](https://img.shields.io/badge/Status-Complete-green)

A high-performance implementation of a **Hopfield Network** using **JIT compilation (Numba)** to model associative memory. This project explores the intersection of statistical physics and computational neuroscience by simulating how biological constraints (inhibitory neurons) affect memory retrieval and system stability.

## Project Overview
This simulation uses the **MNIST dataset** to store and recall handwritten digits. It investigates the system's behavior under three conditions:
1.  **Noise Robustness:** Can the network recall a digit if 40% of the pixels are corrupted?
2.  **Memory Capacity:** How many patterns can be stored before the system creates spurious states (hallucinations)?
3.  **Biological Asymmetry:** Introducing **Dale's Principle** (20% inhibitory neurons) to study its effect on attractor dynamics.

---

## Theoretical Background

The network is modeled as a system of binary spins $s_i \in \{+1, -1\}$ governed by an energy function. The system naturally evolves towards local minima (attractors) in the energy landscape, which correspond to stored memories.

### 1. Energy Function
The scalar energy $E$ of the network state is defined as:
$$E = -\frac{1}{2} \sum_{i,j} w_{ij} s_i s_j$$

### 2. Hebbian Learning
Memories are stored by modifying the synaptic weights $w_{ij}$ according to the outer product of the pattern vectors $\xi$:
$$w_{ij} = \frac{1}{N} \sum_{\mu=1}^{M} \xi_i^{\mu} \xi_j^{\mu}$$

### 3. Dynamics
The state update rule minimizes the energy:
$$s_i(t+1) = \text{sgn}\left( \sum_{j} w_{ij} s_j(t) \right)$$

---

## Key Experiments

### Experiment 1: Phase Transitions
We simulate the "temperature" of the system by injecting noise into the initial states. We observe a ferromagnetic-to-paramagnetic phase transition where recall capability collapses beyond a critical noise threshold ($\approx 0.35$).

### Experiment 2: Complexity Analysis
Using **Sample Entropy (SampEn)**, we analyze the trajectory of the energy function during recall. We find that inhibitory networks often exhibit more complex settling dynamics than standard symmetric networks.

### Experiment 3: Memory Capacity
We test the standard storage limit ($\alpha \approx 0.14N$). The simulation demonstrates that exceeding this load causes "catastrophic forgetting," where the retrieval overlap drops significantly.

---

## Installation & Usage

### 1. Clone the Repository
```bash
git clone [https://github.com/fa-mel/hopfield-network-project.git](https://github.com/fa-mel/hopfield-network-project.git)
cd hopfield-network-project
