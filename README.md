# Modified-Black-Jack_MonteCarlo_and_SARSA
This repo contains the environment, Monte Carlo Control, and Sarsa(λ) implementations using **forward-view** methods only, developed fully in **Jupyter Notebooks**.

---

## Project Overview

The project implements reinforcement learning algorithms on a simplified Blackjack variant (different rules than Sutton & Barto’s example).  
Key components:

### Environment
- Infinite deck, sampled with replacement.
- Cards: values 1–13; colors: **black (2/3)** or **red (1/3)**.
- Player and dealer both start with one **black** card.
- Player may **hit** or **stick**.
- Black cards add value; red cards subtract.
- Player busts if sum < 1 or > 21.
- Dealer policy: hit until sum ≥ 17.
- Dealer simulation is part of the environment.
- No discounting (γ = 1).

A `step()` function is implemented that:
- Accepts a **state** (dealer’s card 1–13, player sum 1–21)  
- Accepts an **action** (hit or stick)  
- Returns **(next_state, reward, terminal_flag)**

---

## Reinforcement Learning Components

### **1️ Monte Carlo Control**
- Uses **ε-greedy** exploration  
  - εₜ = N₀ / (N₀ + N(s)), N₀ = 100 (modifiable)
- Step size αₜ = 1 / N(s, a)
- Estimates **Q\*** and the **optimal value function V\*(s) = maxₐ Q\*(s,a)**.
- Produces a 3D surface plot similar to Sutton & Barto Fig. 5.3 but with dealer showing values **1–13**.

---

### **2️ Sarsa(λ) — Forward View Only**
- λ ∈ {0, 0.1, 0.2, ..., 1}
- Uses same αₜ and εₜ scheduling as MC.
- Runs 1000 episodes per λ.
- Computes Mean-Squared Error:  
  Σₛ,ₐ ( Q(s,a) - Q\*(s,a) )²  
- Plots:
  - MSE vs λ  
  - For λ = 0 and λ = 1: MSE vs episode number (**learning curves**)

---

## Models Implemented

### **Model 1 — Neural Network (NN)**  
Built using TensorFlow/Keras or PyTorch:
- Dense layers  
- ReLU activation  
- Dropout (optional)  
- Sigmoid output for binary classification  

### **Model 2 — Convolutional Neural Network (CNN)**  
CNN applied on reshaped tabular data:
- Conv1D / Conv2D layers  
- MaxPooling layers  
- Flatten + Dense layers  
- Sigmoid output  

### Comparison Included:
- Which model performs better  
- Why based on dataset characteristics  
- Limitations and observations  

---

## Model Training & Evaluation

Metrics used:

- Accuracy  
- Precision  
- Recall  
- F1 Score  
- AUC-ROC Curve  
- Confusion Matrix  

---

## How to Run the Project

1. Clone the repository:

```bash
git clone <repo-url>
cd Modified-Black-Jack_MonteCarlo_and_SARSA
```

2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Start Jupyter Notebook:

```bash
jupyter notebook
```

4. Open the .ipynb file 

---
