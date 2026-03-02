# Statistical Modelling and Anomaly Detection in Medical Data

A learning and applied portfolio project combining mathematics, 
statistics, and Python to study how abnormal patterns can be 
detected in data — with a focus on medical and physiological signals.

---

## Motivation

Medical data are often noisy, incomplete, and difficult to interpret —
especially in low-resource settings. This project applies statistical 
modelling to the problem of anomaly detection: first characterizing 
what "normal" data look like, then identifying observations that 
deviate significantly from that model.

This is a training project, built step by step, with the dual goal of 
strengthening applied mathematics skills and building a first 
structured data science portfolio.

---

## Research Question

How can medical data be statistically modelled in order to characterize 
their normal behavior and automatically identify atypical observations, 
while taking into account noise, variability, and missing values?

---

## Methods

The project follows a progressive approach:

1. **Z-score detection** — baseline statistical method using mean and 
   standard deviation
2. **Robust statistics (MAD)** — median-based method, more resistant 
   to the influence of outliers
3. **Isolation Forest** — unsupervised machine learning baseline for 
   comparison

---

## Project Structure
```
medical-anomaly-detection/
├── notebooks/        # Jupyter notebooks, one per method
├── data/
│   ├── raw/          # Original datasets, untouched
│   └── processed/    # Cleaned data ready for analysis
├── figures/          # Saved plots and visualizations
├── report/           # Final written summary
├── requirements.txt  # Python dependencies
└── README.md
```

---

## Tools

- Python 3
- NumPy
- Pandas
- Matplotlib
- Scikit-learn

---

## Status

| Stage | Description | Status |
|---|---|---|
| 1 | Repository setup | ✅ Done |
| 2 | Z-score on synthetic data | 🔄 In progress |
| 3 | Robust statistics (MAD) | ⏳ Planned |
| 4 | Isolation Forest + comparison | ⏳ Planned |

---

## Author

Mathematics teacher and bachelor in mathematics, currently building 
skills in applied statistics and data science. This project is part 
of my preparation for a master's program in applied mathematics 
and data science.
```

