# CKD Predictor 🩺

A web-based predictive analytic system for early detection of **Chronic Kidney Disease (CKD)** using an ensemble-based machine learning model. This project is based on the IEEE conference paper:

> **"Development of a Predictive Analytic System for Chronic Kidney Disease using Ensemble-based Machine Learning"**
> Zobair Hasan, Rafiur Rahman Khan, Wazed Rifat, Dipok Sorkar Dipu, Muhammad Nazrul Islam, Dr. Iqbal H. Sarker
> *IEEE ITMS 2021* — DOI: [10.1109/ITMS52826.2021.9615273](https://doi.org/10.1109/ITMS52826.2021.9615273)

---

## Overview

CKD is a progressive disease where kidney function deteriorates over months to years, often with no visible symptoms in early stages. Early detection significantly reduces treatment cost and improves patient outcomes. This system enables both patients and healthcare professionals to predict CKD risk by entering clinical data through a simple web interface.

---

## Model

The predictor uses an **Ensemble Voting Classifier** combining seven machine learning algorithms selected based on highest accuracy and lowest false negative error:

| Algorithm | Accuracy | False Negatives |
|---|---|---|
| Logistic Regression | 94.17% | 2 |
| Decision Tree | 97.5% | 1 |
| SVM | 97.5% | 1 |
| Random Forest | 99.17% | 1 |
| Gradient Boosting | 98.33% | 0 |
| CNN (MLP) | 97.5% | 3 |
| Naive Bayes | 94.17% | 7 |
| **Ensemble (all 7)** | **99.17%** | **0** |

The final ensemble model achieves **99.17% accuracy with zero false negative errors** on the UCI CKD dataset.

---

## Dataset

- Source: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/chronic_kidney_disease)
- 400 instances collected from Apollo Hospitals, Tamilnadu, India
- 24 features (10 categorical + 14 numerical)
- Target: `ckd` or `notckd`
- Missing values filled with column mean; numerical features scaled to [0, 1] using min-max normalization
- Train/test split: 70/30

---

## Features Used

**Numerical:** Age, Blood Pressure, Specific Gravity, Albumin, Sugar, Blood Glucose Random, Blood Urea, Serum Creatinine, Sodium, Potassium, Hemoglobin, Packed Cell Volume, WBC Count, RBC Count

**Categorical:** Red Blood Cells, Pus Cell, Pus Cell Clumps, Bacteria, Hypertension, Diabetes Mellitus, Coronary Artery Disease, Appetite, Pedal Edema, Anemia

---

## Tech Stack

- **Backend:** Python, Flask
- **ML Model:** scikit-learn (Ensemble Voting Classifier), saved as `evc.pickle`
- **Frontend:** HTML, CSS, JavaScript

---

## Project Structure

```
CKD-predictor/
├── app.py               # Flask application
├── evc.pickle           # Trained ensemble model
├── requirements.txt     # Python dependencies
├── Procfile             # Deployment config
├── static/              # CSS, JS, images
└── templates/           # HTML templates
    ├── index.html       # Input form
    └── result.html      # Prediction result page
```

---

## Getting Started

**1. Clone the repository**
```bash
git clone https://github.com/Zobair1234/CKD-predictor.git
cd CKD-predictor
```

**2. Install dependencies**
```bash
pip install -r requirements.txt
```

**3. Run the app**
```bash
python app.py
```

**4. Open in browser**
```
http://localhost:5000
```

---

## Usage

Enter the patient's clinical values into the form (all 24 features). The system scales the inputs and runs them through the ensemble model, then displays whether the patient is predicted to have CKD or not.

---

## Citation

If you use this work, please cite:

```bibtex
@inproceedings{hasan2021ckd,
  title={Development of a Predictive Analytic System for Chronic Kidney Disease using Ensemble-based Machine Learning},
  author={Hasan, Zobair and Khan, Rafiur Rahman and Rifat, Wazed and Dipu, Dipok Sorkar and Islam, Muhammad Nazrul and Sarker, Iqbal H.},
  booktitle={2021 IEEE International Conference on Innovative Trends in Multidisciplinary Academic Research (ITMS)},
  year={2021},
  doi={10.1109/ITMS52826.2021.9615273}
}
```

---

## Authors

- **Zobair Hasan** — [GitHub](https://github.com/Zobair1234)
- Rafiur Rahman Khan
- Wazed Rifat
- Dipok Sorkar Dipu
- Muhammad Nazrul Islam — Military Institute of Science and Technology
- Dr. Iqbal H. Sarker — Chittagong University of Engineering and Technology
