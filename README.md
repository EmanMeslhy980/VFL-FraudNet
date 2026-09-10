# VFL-FraudNet
# VFL-FraudNet: Healthcare Fraud Detection using Vertical Federated Learning

This repository contains the implementation of a healthcare fraud detection system using **Vertical Federated Learning (VFL)**. 
The system trains an AI model on data distributed across multiple parties (hospitals, insurance companies, pharmacies) **without sharing raw data**, while ensuring privacy and resistance to malicious attacks.

## 🚀 Key Features
- **Vertical Federated Learning (VFL):** Data is partitioned feature-wise across 3 parties (Hospital, Insurance, Pharmacy) to train a unified model.
- **Byzantine Robustness:** Integration of `Zero-Trust` technique with the `Krum` algorithm for effective defense against Gradient Poisoning Attacks.
- **Risk-Aware Layer:** Enhances the model's ability to detect complex patterns and rare fraud cases.
- **Differential Privacy:** Applies clipping and perturbation (Clipping & Perturbation) to protect model updates.

## 📦 Requirements
To run the code, make sure the following libraries are installed:
```bash
pip install torch pandas numpy scikit-learn matplotlib
<img width="1408" height="768" alt="Model" src="https://github.com/user-attachments/assets/f314d7c4-4ce9-409e-b3d2-b367be8b5a6a" />
