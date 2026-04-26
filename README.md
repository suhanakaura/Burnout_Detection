# Machine Learning Based Early Detection of Burnout in Young Adults

**Author:** Suhana Kaura | Roll No: 2210992414
**Program:** BE — Computer Science and Engineering
**Institution:** Chitkara University, Rajpura, Punjab
**Contact:** suhana2414.be22@chitkara.edu.in

---

## Overview

This project trains three machine learning classifiers — Logistic Regression, Random Forest, and SVM — to classify burnout risk in young adults as **Low**, **Moderate**, or **High**. The model is trained on the publicly available Student Stress Factors dataset from Kaggle (1,100 student records). Random Forest achieves the best performance with **93.6% accuracy** and a **93.5% weighted F1-score**.

---

## Repository Structure

```
burnout-detection/
│
├── burnout_detection.py      # main source code — run this
├── requirements.txt          # Python dependencies
├── README.md                 # this file
│
├── StressLevelDataset.csv    # dataset — download separately (see below)
│
└── outputs/                  # auto-created when you run the code
    ├── fig1_confusion_matrices.png
    ├── fig2_model_comparison.png
    ├── fig3_feature_importance.png
    ├── fig4_roc_curves.png
    ├── fig5_dataset_overview.png
    ├── fig6_cross_validation.png
    ├── fig7_feature_distributions.png
    └── burnout_charts.zip
```

---

## Dataset

**Name:** Student Stress Factors — A Comprehensive Analysis
**Source:** Kaggle
**Link:** https://www.kaggle.com/datasets/rxnach/student-stress-factors-a-comprehensive-analysis
**Size:** 1,100 student records | 21 features | 3 stress level labels (0, 1, 2)

### How to download

1. Go to the Kaggle link above
2. Click **Download** (you need a free Kaggle account)
3. Extract and place `StressLevelDataset.csv` in the same folder as `burnout_detection.py`

---

## How to Run

### Option A — Local (Python)

**Step 1: Clone the repository**
```bash
git clone https://github.com/suhanakaura/Burnout_Detection.git
cd burnout-detection
```

**Step 2: Install dependencies**
```bash
pip install -r requirements.txt
```

**Step 3: Place the dataset**

Download `StressLevelDataset.csv` from Kaggle and place it in the project folder.

**Step 4: Run**
```bash
python burnout_detection.py
```

All 7 charts will be saved to the `outputs/` folder automatically.

---

### Option B — Google Colab

1. Open [colab.research.google.com](https://colab.research.google.com)
2. Upload `burnout_detection.py`
3. Upload `StressLevelDataset.csv` using the Files panel (left sidebar)
4. Add this cell at the top and run it first:
   ```python
   !pip install scikit-learn pandas numpy matplotlib seaborn --quiet
   ```
5. Run the script — charts will download automatically as `burnout_charts.zip`

---

## Feature Mapping

The 21-column Kaggle dataset was mapped to 10 interpretable features aligned with the study's questionnaire:

| Derived Feature | Source Column | Encoding Range |
|---|---|---|
| sleep_hours | sleep_quality | 1–3 |
| sleep_deprivation | sleep_quality (inverted) | 1–5 |
| study_hours | study_load | 1–4 |
| overwhelmed | academic_performance (inverted) | 1–5 |
| stress_level | depression | 1–5 |
| emotional_exhaust | depression | 1–5 |
| unmotivated | self_esteem (inverted) | 1–5 |
| exercise_week | extracurricular_activities | 0–3 |
| screen_hours | future_career_concerns | 2–4 |
| mental_fatigue | mental_health_history | 1 or 3 |

---

## Results

| Model | Accuracy | Precision | Recall | F1-Score | CV Accuracy |
|---|---|---|---|---|---|
| Logistic Regression | 84.5% | 84.6% | 84.5% | 84.4% | 84.3% ± 1.8% |
| SVM (RBF) | 89.1% | 89.2% | 89.1% | 89.1% | 91.0% ± 1.4% |
| **Random Forest** | **93.6%** | **93.7%** | **93.6%** | **93.5%** | **93.1% ± 1.2%** |

Random Forest outperforms both baselines. Feature importance analysis confirms that **stress level** and **emotional exhaustion** are the strongest predictors, consistent with the Maslach Burnout Inventory framework.

---

## Pipeline Summary

```
Raw Dataset (Kaggle, 1100 records, 21 features)
        |
Feature Mapping (10 features selected and normalised)
        |
Labels: 0 = Low Risk | 1 = Moderate Risk | 2 = High Risk
        |
Train/Test Split: 80% Train (880) / 20% Test (220), Stratified
        |
StandardScaler (fitted on train only)
        |
Model Training: Logistic Regression | Random Forest | SVM (RBF)
        |
Evaluation: Accuracy, Precision, Recall, F1, ROC-AUC, 5-Fold CV
        |
Best Model: Random Forest (Acc: 93.6%, F1: 93.5%)
        |
Output: Low / Moderate / High Burnout Risk
```

---

## Dependencies

```
scikit-learn >= 1.3.0
pandas       >= 2.0.0
numpy        >= 1.24.0
matplotlib   >= 3.7.0
seaborn      >= 0.12.0
```

Install all at once:
```bash
pip install -r requirements.txt
```

---

## Research Paper

The full research paper submitted alongside this code:

**Title:** Machine Learning Based Early Detection of Burnout in Young Adults
**Author:** Suhana Kaura, Chitkara University
**File:** `2210992414_BurnoutDetection.docx`

---

## Acknowledgment

This project was conducted as part of undergraduate coursework at Chitkara University and received no external funding. The dataset used is publicly available on Kaggle under the title *Student Stress Factors: A Comprehensive Analysis* (rxnach/student-stress-factors-a-comprehensive-analysis). The author thanks the dataset creator for making it openly accessible for academic research.
