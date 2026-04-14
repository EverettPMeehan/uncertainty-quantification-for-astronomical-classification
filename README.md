# Stellar UQ — Uncertainty-Aware Classification of Astronomical Objects
 
> **Status: Pre-development** — This repository is a placeholder. Active development begins soon.
 
---
 
## Overview
 
A machine learning project that classifies astronomical objects (stars, galaxies, quasars) from SDSS spectroscopic and photometric data — with a focus on **calibrated uncertainty quantification**.
 
Most classifiers tell you *what* an object is. This project asks a harder question: **does the model know when it doesn't know?** Overconfident predictions in scientific pipelines are a real problem. An AI system that assigns 99% confidence to a misclassified rare transient is more dangerous than one that says "I'm unsure." This project treats honest uncertainty as a first-class output.
 
---
 
## Research Questions
 
1. How well-calibrated are standard ML classifiers on astronomical object data?
2. Do uncertainty estimates increase meaningfully for out-of-distribution (OOD) objects (rare transients, edge-case spectra)?
3. Which UQ method — MC Dropout, Conformal Prediction, or Gaussian Processes — best signals genuine model uncertainty without sacrificing accuracy?
4. Can we build a taxonomy of *how* overconfidence manifests in this domain?
 
---
 
## Planned Approach
 
### Data
- **Source**: SDSS DR17 via `astroquery` (~50k+ labeled objects: stars, galaxies, quasars)
- **Features**: Photometric magnitudes (u, g, r, i, z), spectroscopic features, redshift
- **OOD test set**: Rare transients from TESS/ZTF, synthetic perturbations
 
### Methods
| Method | Library | What it gives |
|---|---|---|
| MC Dropout | PyTorch | Predictive variance via stochastic forward passes |
| Conformal Prediction | MAPIE | Coverage-guaranteed prediction sets |
| Gaussian Process | GPyTorch | Full posterior uncertainty estimates |
 
### Evaluation
- Reliability diagrams (calibration curves)
- Expected Calibration Error (ECE)
- OOD uncertainty response: does confidence drop on unknown object types?
- Failure taxonomy: systematic audit of overconfident misclassifications
 
---
 
## Planned Stack
 
```
Python · PyTorch · scikit-learn · MAPIE · GPyTorch
astroquery · pandas · NumPy · Plotly · Streamlit
```
 
---
 
## Roadmap
 
- [ ] Week 1–2: Data pipeline + baseline classifier
- [ ] Week 3–4: Implement MC Dropout, Conformal Prediction, GP
- [ ] Week 5–6: OOD stress-testing + failure analysis
- [ ] Week 7: Write-up, demo, and publish
 
---
 
## Motivation
 
This project sits at the intersection of applied ML and AI safety research. Uncertainty quantification is not just a performance metric — it is a property of *trustworthy* systems. A model that knows its own limitations is safer to deploy than one that doesn't. The astronomical domain makes this concrete: misclassifying a rare transient with high confidence could mean a missed discovery. The same principle applies anywhere AI systems make high-stakes decisions.
 
---
 
## Demo
 
*Coming soon — a Streamlit/HuggingFace Spaces app where you can upload a spectrum and receive a classification with calibrated uncertainty estimates.*
 
---
 
## Author
 
Everett — Data Science & Mathematics, Northeastern University  
Interests: AI safety, alignment, ML systems, astrophysics data
 
---
 
*This README will be updated as development progresses.*
