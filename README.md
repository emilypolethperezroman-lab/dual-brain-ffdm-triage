# Dual-Brain Mammography Pipeline with Bayesian Uncertainty

An auditable and reproducible full-field digital mammography (FFDM) triage workflow designed to mitigate dataset and acquisition shifts in screening programs.

## 🧠 Architecture Overview
The system deconstructs the classification problem into two complementary pathways:
* **Brain A (ConvNeXt-Tiny):** Learns deep hierarchical spatial representations from raw tensors.
* **Brain B (Radiomics + XGBoost):** Maps handcrafted intensity, texture, and morphological descriptors (e.g., GLCM, Shannon Entropy).
* **Fusion Layer:** A calibration-only logistic stacking layer trained on internal validation predictions to suppress acquisition-shift false positives.

## 🛡️ Key Features
* **Bayesian Uncertainty Quantification:** Integrates Monte Carlo (MC) Dropout ($T=30$ forward passes) to isolate epistemic and aleatoric uncertainty via predictive entropy and mutual information.
* **Explainable AI (XAI):** Post-hoc audits featuring Grad-CAM spatial attribution, radiomics feature importance, and false-color intensity mappings.
* **Rigorous Domain Validation:** Evaluated via a strictly locked external gate on the Mexican Mammo-MX dataset ($1,000$ images).

## 📊 Promoted Gate Results (Mammo-MX)
* **ROC-AUC:** 0.8728 
* **PR-AUC:** 0.8371
* **Sensitivity:** 0.8600 
* **Specificity:** 0.7017
* **Expected Calibration Error (ECE):** 0.0437

---
> This system is a traceable research workflow for uncertainty-aware triage, not a standalone diagnostic tool.
