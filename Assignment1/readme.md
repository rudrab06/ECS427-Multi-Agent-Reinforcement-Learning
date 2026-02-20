📘 Multi-Agent Reinforcement Learning – Assignment 1

This repository contains the implementation and analysis of three Markov Decision Process (MDP) problems solved using:

✅ Value Iteration

✅ Policy Iteration

✅ Monte Carlo Methods

The project focuses on robotics-oriented decision making under uncertainty.

📂 Repository Structure
.
├── marl_assignment1.py          # Main implementation
├── assign1.pdf                  # Final report
├── manual_derivations.pdf       # Handwritten Bellman derivations (3×3 grid)
├── convergence_plot.png
├── orientation_aware_10.png
├── policy_risk_0_1.png
├── policy_risk_0_3.png
├── ...
└── README.md
🧠 Problem Overview
🔹 Question 1 – Orientation-Aware Navigation

State: 
𝑠
=
(
𝑥
,
𝑦
,
𝜃
)
s=(x,y,θ)

Actions: Forward, TurnLeft, TurnRight

Stochastic forward motion (slip probability)

Collision and goal terminal states

Key Insight:

Including orientation in the state space fundamentally changes policy structure.

🔹 Question 2 – Battery-Aware Navigation

State: 
𝑠
=
(
𝑥
,
𝑦
,
𝑏
)
s=(x,y,b)

Recharge action available at charging stations

Terminal failure if battery depletes

Key Insight:

Battery-awareness emerges naturally from reward optimization.

🔹 Question 3 – Risk-Sensitive Navigation

Hazard zones with slip probability

Catastrophic penalty (-200)

Risk-adjusted decision-making

Key Insight:

Shortest path is not always optimal under stochastic risk.

⚙️ Algorithms Implemented
1️⃣ Value Iteration

Bellman Optimality Update:

𝑉
𝑘
+
1
(
𝑠
)
=
max
⁡
𝑎
∑
𝑠
′
𝑃
(
𝑠
′
∣
𝑠
,
𝑎
)
[
𝑅
+
𝛾
𝑉
𝑘
(
𝑠
′
)
]
V
k+1
	​

(s)=
a
max
	​

s
′
∑
	​

P(s
′
∣s,a)[R+γV
k
	​

(s
′
)]

Converges in 89 iterations (10×10 grid)

Memory efficient

Simpler update rule

2️⃣ Policy Iteration

Alternates between:

Policy Evaluation

Policy Improvement

Converges in 9 improvement steps

Higher memory usage (stores value + policy)

Fewer outer iterations but heavier computation per step

3️⃣ Monte Carlo

Model-free

Requires many episodes

Useful when transition model is unknown

📊 Experimental Results (10×10 Grid)
Method	Iterations	Runtime (sec)	Memory (bytes)
Value Iteration	89	~0.15	51968
Policy Iteration	9	~0.34	113486
Observations:

VI requires more iterations but runs faster.

PI converges in fewer steps but consumes more memory.

Model-based methods outperform Monte Carlo in convergence speed.

📈 Convergence Behavior

Convergence plots are included for:

Q1 (Orientation-aware)

Q2 (Battery-aware)

Q3 (Risk-sensitive)

Bellman error decreases monotonically, confirming correctness.

🧪 Manual Verification

To validate correctness:

A reduced 3×3 grid was used.

First three Bellman updates were computed manually.

Handwritten derivations are included in manual_derivations.pdf.

This verifies correctness before scaling to the full 10×10 grid.

🏗️ How to Run
python marl_assignment1.py

The script:

Runs Value Iteration

Runs Policy Iteration

Compares runtime & memory

Generates policy visualizations

Plots convergence graphs

🎯 Key Takeaways

State representation critically affects optimal policy.

Long-term penalties significantly alter behavior.

Risk and uncertainty invalidate shortest-path intuition.

Reward design strongly influences emergent behavior.

📚 Course

Multi-Agent Reinforcement Learning
Assignment 1
