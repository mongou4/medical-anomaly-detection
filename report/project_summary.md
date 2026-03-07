# Project Summary — Statistical Modelling and Anomaly Detection in Medical Data

**Author:** Mongou Loic  
**Type:** Learning and applied portfolio project  
**Tools:** Python, NumPy, Pandas, Matplotlib, Scikit-learn  

---

## Research Question

How can medical data be statistically modelled in order to 
characterize their normal behavior and automatically identify 
atypical observations, while taking into account noise, 
variability, and missing values?

---

## Motivation

Medical data play a central role in healthcare decision-making. 
In many contexts — especially in low-resource settings — data 
are often noisy, incomplete, or difficult to interpret, yet the 
decisions based on them are critical.

This project applies statistical modelling to the problem of 
anomaly detection: first characterizing what normal data look 
like, then identifying observations that deviate significantly 
from that model.

---

## Methods

### 1. Z-Score Detection
The classical baseline. For each observation x, we compute:
```
Z = (x - μ) / σ
```

An observation is flagged as anomalous if |Z| > 3.

**Limitation:** Both the mean μ and standard deviation σ are 
sensitive to the very anomalies we are trying to detect. 
This can inflate the boundaries and reduce sensitivity.

---

### 2. Robust Statistics — MAD
The Median Absolute Deviation replaces sensitive statistics 
with robust alternatives:
```
MAD = median(|x - median(x)|)
Modified Z = 0.6745 × (x - median(x)) / MAD
```

The median is not affected by extreme values, making the 
boundaries tighter and more accurate.

---

### 3. Isolation Forest
An unsupervised machine learning method that requires no 
distributional assumption. It isolates anomalies by building 
random decision trees and measuring how quickly each point 
gets isolated.

- Short isolation path → anomaly
- Long isolation path → normal observation

---

## Data

All three notebooks use synthetic data simulating patient 
heart rates:

- 200 normal observations drawn from N(70, 5²)
- 10 injected anomalies: 5 around 40 bpm, 5 around 110 bpm
- Total: 210 observations

The same dataset is used across all three notebooks to ensure 
fair comparison.

---

## Results

| Method | True Positives | False Positives | False Negatives |
|---|---|---|---|
| Z-Score | 10 | 0 | 0 |
| MAD | 10 | 0 | 0 |
| Isolation Forest | 9 | 2 | 1 |

All three methods successfully detected most injected anomalies. 
On this clean synthetic dataset, Z-Score and MAD achieved 
perfect detection. Isolation Forest produced 2 false positives 
and missed 1 anomaly.

---

## Key Findings

**1. The standard deviation is distorted by anomalies.**  
When anomalies are present, the standard deviation increased 
from 5 (the true value) to 9. This inflates the detection 
boundaries and can cause the method to miss subtle anomalies.

**2. MAD boundaries are tighter and more reliable.**  
The median stayed close to 70 even with 10 anomalies injected. 
The MAD boundaries accurately reflected the true variability 
of the normal data.

**3. Isolation Forest is powerful but less precise on simple data.**  
Its advantage will emerge on real multivariate data where 
distributions are unknown and complex.

---

## Honest Limitations

- All methods were tested on synthetic data only
- Anomalies were deliberately obvious
- The study is one-dimensional
- Results on real physiological data may differ significantly

---

## Next Steps

The natural continuation of this project is to apply these 
methods to real open physiological datasets from PhysioNet, 
where data are noisy, multivariate, and anomalies are not 
known in advance. This will test whether the conclusions 
from synthetic data hold in a realistic setting.

---

## Project Structure
```
medical-anomaly-detection/
├── notebooks/
│   ├── 01_zscore_detection.ipynb
│   ├── 02_robust_statistics.ipynb
│   └── 03_isolation_forest.ipynb
├── figures/
│   ├── fig01_data_overview.png
│   ├── fig02_zscore_results.png
│   ├── fig03_mad_comparison.png
│   ├── fig04_isolation_forest.png
│   └── fig05_final_comparison.png
├── data/
│   ├── raw/
│   └── processed/
├── report/
│   └── project_summary.md
├── requirements.txt
└── README.md
```
