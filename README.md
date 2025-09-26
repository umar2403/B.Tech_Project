# Experimenting Q-Learning with Function Approximation

This repository contains the implementation and experiments for applying **Q-Learning** using both **tabular methods** and **function approximation**. The project explores how different learning rate strategies (constant vs. Robbins-Monro schedules) affect convergence, accuracy, and computational efficiency in a controlled Markov Decision Process (MDP) setup.  

## 📘 Project Overview
- Implemented **Vanilla Q-Learning** with:
  - Constant learning rate  
  - Robbins-Monro diminishing learning rate  
- Extended to **Function Approximation** using:
  - 10th-degree polynomial features  
  - Constant and Robbins-Monro learning rates  
- Compared performance in terms of:
  - Convergence speed  
  - Accuracy (MSE against Dynamic Programming solutions)  
  - Runtime efficiency  

## 🧩 Key Concepts
- **Markov Decision Process (MDP):** Provides the foundation for the environment with defined states, actions, rewards, and transition dynamics.  
- **Q-Learning:** A model-free reinforcement learning algorithm used to approximate the optimal action-value function.  
- **Function Approximation:** Used polynomial features to replace large Q-tables, enabling scalability and generalization.  
- **Robbins-Monro Algorithm:** An adaptive learning rate schedule that improves stability and convergence.  

## ⚙️ Implementation Details
- **Language:** MATLAB  
- **Environment Setup:**
  - State space: \( S = \{0, 1,...., p-1\} \), with \( p = 100 \)  
  - Action space: \( A = \{0, 1,...., p-1\} \)  
  - Transition dynamics:  
    \[
    s_{t+1} = (s_t + a_t + n_t) \mod p
    \]  
    where noise \( n_t \) is uniformly sampled.  
  - Reward function:  
    \[
    R(s, a) = s.a
    \]  
- **Exploration Strategy:** ε-greedy policy  
- **Discount Factor:** γ = 0.9  

## 📊 Results
- **Vanilla Q-Learning (constant α):** Slow convergence, high RMS error (~6000)  
- **Q-Learning (Robbins-Monro α):** Faster convergence, lower RMS error (~199)  
- **Function Approximation (constant α):** Unstable convergence, RMS error ~6000  
- **Function Approximation (Robbins-Monro α):** Fast convergence, RMS error ~1673  

| Algorithm | Runtime (s) | Convergence (iterations) | RMS Error |
|-----------|-------------|---------------------------|-----------|
| Vanilla Q-Learning | 2137 | \(1 \times 10^8\) | 6000 |
| Q-Learning + Robbins-Monro | 996 | \(5 \times 10^7\) | 199 |
| Function Approximation (Constant α) | 1115 | \(5 \times 10^7\) | 6000 |
| Function Approximation (Robbins-Monro α) | 570 | \(3 \times 10^7\) | 1673 |
