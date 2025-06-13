# smart-grid-drl
 Smart Grid Optimization Using Deep Reinforcement Learning (PPO + Edge Computing)

This project demonstrates an AI-based demand response system for smart grids using **Deep Reinforcement Learning (PPO)**. The objective is to reduce energy costs and balance consumption dynamically in response to changing energy demand and renewable generation.

 Project Overview

-  **Model**: Proximal Policy Optimization (PPO) via Stable-Baselines3  
-  **Scenario**: Smart home with appliances + varying energy prices + solar energy  
-  **Goal**: Minimize cost by scheduling appliance usage smartly  
-  **Tooling**: Python, Gymnasium, Stable-Baselines3, Google Colab  
-  **Approach**: Build a Gym environment, train PPO agent, evaluate performance  
-  **Extension**: Can scale to multi-home grid + federated learning

---

 Project Structure

| File / Folder | Description |
|---------------|-------------|
| `smart_grid_drl.ipynb` | Main Colab notebook with code and training |
| `ppo_smart_grid_model.zip` | Trained PPO model |
| `data/` | Dataset used (smart home energy usage etc.) |
| `images/` | Visuals, charts, diagrams for presentation |
| `report.pdf` *(optional)* | Research document / paper |
| `README.md` | This file |

---

  Dataset

We used publicly available smart home datasets with:
- Time-of-use electricity pricing
- Weather conditions
- Appliance power consumption (kW)
- Solar power generation

Example sources:
- UCI Smart Home dataset
- UK Domestic Appliance-Level Electricity (UK-DALE)
- Synthetic smart home data

---

 Methodology

-  **Environment**: Custom-built `SmartHomeEnv` class (OpenAI Gym-style)
-  **Agent**: Trained using PPO from Stable-Baselines3
-  **Reward Function**: Penalizes high energy cost, rewards optimal appliance use
-  **Training**: 50k+ time steps, policy improvement via clipped surrogate objective
-  **Edge Computing (Conceptual)**: Fast inference for real-time control on edge devices

---

 Results

| Metric | Value |
|--------|-------|
| Mean Squared Error | `~0.00398` |
| Total Energy Cost (Optimized) | `≈ 4.34` |
| Cost Reduction (vs Baseline) | ~50% |
| Latency (in real edge setup) | ~1-2 seconds (theoretical) |

---

 How to Use

1. Clone the repo or open the `.ipynb` notebook in [Google Colab](https://colab.research.google.com/)
2. Run each cell to train and evaluate the PPO agent
3. Modify `SmartHomeEnv` for different appliances or conditions
4. To load a pre-trained model:
```python
from stable_baselines3 import PPO
model = PPO.load("ppo_smart_grid_model")
