# Multi-Agent Reinforcement Learning – Assignment 1

This repository contains the implementation and analysis of three Markov Decision Process (MDP) problems solved using:

- Value Iteration
- Policy Iteration
- Monte Carlo Methods

The assignment focuses on robotics-oriented decision making under uncertainty.

---

# Repository Structure

.
├── marl_assignment1.ipynb  
├── assign1.pdf  
├── manual_derivations.pdf  
├── convergence_plot.png  
├── orientation_aware_10.png  
├── policy_risk_0_1.png  
├── policy_risk_0_3.png  
└── README.md  

---

# Question 1 – Orientation-Aware Navigation

State:
s = (x, y, θ)

- x, y are grid coordinates  
- θ ∈ {0, π/2, π, 3π/2} represents orientation  

Actions:
- Forward  
- TurnLeft  
- TurnRight  

Forward action is stochastic:
- 0.8 probability intended movement  
- 0.1 slip left  
- 0.1 slip right  

Collision and goal states are terminal.

### Implementation Note

A reduced 3×3 grid was first implemented to manually verify the first three iterations of Value Iteration and Policy Iteration.  
After confirming correctness, the same algorithm was extended to the full 10×10 grid for final experiments.

### Key Insight

Including orientation in the state space significantly changes the structure of the optimal policy.

---

# Question 2 – Battery-Aware Navigation

State:
s = (x, y, b)

- b represents battery level  

Actions:
- MoveUp  
- MoveDown  
- MoveLeft  
- MoveRight  
- Recharge  

Battery depletion away from charging stations leads to a terminal failure state.

### Key Insight

Battery-aware behavior emerges automatically from reward optimization without explicitly programming safety rules.

---

# Question 3 – Risk-Sensitive Navigation

State:
s = (x, y, h)

- h indicates proximity to a hazardous region  

Near hazards, actions may slip into a catastrophic terminal state.

### Key Insight

Shortest path intuition fails under stochastic risk.  
The agent selects longer but safer paths when catastrophic penalties dominate expected return.

---

# Algorithms Implemented

## Value Iteration

Bellman Optimality Update:

V_{k+1}(s) = max_a Σ P(s'|s,a) [ R + γ V_k(s') ]

For the 10×10 grid:
- Iterations: 89  
- Runtime: ~0.15 sec  
- Memory: 51968 bytes  

Value Iteration requires more iterations but each update is computationally simple.

---

## Policy Iteration

Alternates between:
- Policy Evaluation  
- Policy Improvement  

For the 10×10 grid:
- Policy improvement steps: 9  
- Runtime: ~0.34 sec  
- Memory: 113486 bytes  

Policy Iteration converges in fewer outer iterations but requires more memory because it stores both the value function and the policy table.

---

## Monte Carlo Method

- Model-free approach  
- Uses sampled episodes  
- Requires many episodes for convergence  

Monte Carlo is useful when transition probabilities are unknown, but it is slower compared to model-based dynamic programming methods.

---

# Convergence and Visualization

The notebook includes:

- Bellman error convergence plots  
- Orientation-aware policy visualization  
- Battery-aware policy visualization  
- Risk-sensitive policy comparison (different slip probabilities)  
- Monte Carlo comparison  

---

# Manual Verification

To validate correctness:

- A 3×3 grid was used to compute the first three Bellman updates manually.
- Handwritten derivations are included in `manual_derivations.pdf`.

This verifies correctness before scaling to the 10×10 environment.

---

# How to Run

## Option 1 – Jupyter Notebook (Recommended)

Open:

marl_assignment1.ipynb

Run all cells sequentially.

The notebook:
- Runs Value Iteration  
- Runs Policy Iteration  
- Compares runtime and memory  
- Generates convergence plots  
- Visualizes optimal policies  

## Option 2 – Exported Script (if applicable)

If converted to Python:

python marl_assignment1_22268.py

---

# Summary

This project demonstrates how:

- State representation affects optimal behavior.
- Reward structure influences emergent decision-making.
- Risk and uncertainty alter shortest-path intuition.
- Model-based methods converge faster than sampling-based approaches.

---

Course: Multi-Agent Reinforcement Learning  
Assignment 1  
Author: Rudra Baunk
