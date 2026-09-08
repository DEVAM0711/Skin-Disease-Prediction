# 🧫 Skin Disease Prediction 

## 📌 Project Overview

This project develops a **machine-learning classification system for predicting six classes of erythemato-squamous skin diseases** using clinical and histopathological features.

The project covers the complete machine-learning workflow:

- Data understanding
- Data cleaning and preprocessing
- Exploratory Data Analysis (EDA)
- Feature analysis
- Correlation analysis
- Train-test splitting
- Model building
- Model comparison
- Cross-validation
- Hyperparameter tuning
- Model evaluation
- Feature importance
- ROC-AUC analysis
- Sample prediction
- Early-identification decision support

> **Important:** This project is intended for educational and decision-support purposes. It is not a substitute for professional medical diagnosis or treatment.

---

## 🎯 Problem Statement

Skin diseases can have similar clinical and histopathological characteristics, making classification challenging.

The objective of this project is to build a machine-learning model that can classify a patient's feature set into one of **six disease classes**.

---

## 📊 Dataset

The dataset contains:

- **366 records**
- **34 input features**
- **1 target variable**
- **6 classes**

### Target Classes

| Class | Percentage |
|---|---:|
| 1 | 30.60% |
| 2 | 16.67% |
| 3 | 19.67% |
| 4 | 13.39% |
| 5 | 14.21% |
| 6 | 5.46% |

The dataset contains clinical and histopathological features such as:

- erythema
- scaling
- definite borders
- itching
- koebner phenomenon
- polygonal papules
- follicular papules
- oral mucosal involvement
- knee and elbow involvement
- scalp involvement
- family history
- melanin incontinence
- eosinophils in the infiltrate
- PNL infiltrate
- fibrosis of the papillary dermis
- exocytosis
- acanthosis
- hyperkeratosis
- parakeratosis
- clubbing of the rete ridges
- elongation of the rete ridges
- thinning of the suprapapillary epidermis
- spongiform pustule
- munro microabcess
- focal hypergranulosis
- disappearance of the granular layer
- vacuolisation and damage of basal layer
- spongiosis
- saw-tooth appearance of retes
- follicular horn plug
- perifollicular parakeratosis
- inflammatory monoluclear infiltrate
- band-like infiltrate
- Age

---

## 🧹 Data Preprocessing

### Missing Values

The original `Age` column contained `?` values.

There were **8 missing Age records**.

The Age feature was converted to numeric format and missing values were handled during preprocessing.

### Duplicate Records

No duplicate records were found.

```text
Duplicate Rows: 0
```

### Final Dataset

```text
Shape: 366 × 35
Features: 34
Target: class
```

---

## 🔎 Exploratory Data Analysis

The project includes analysis of:

### Class Distribution

The dataset is imbalanced, with Class 1 having the highest number of records and Class 6 having the fewest.

### Age Analysis

```text
Mean  : 36.27
Median: 35
Min   : 0
Max   : 75
```

### Feature Analysis

Class-wise feature means were analyzed to identify features that differ across disease classes.

The largest class-mean differences included:

- band-like infiltrate
- vacuolisation and damage of basal layer
- saw-tooth appearance of retes
- fibrosis of the papillary dermis
- polygonal papules
- elongation of the rete ridges
- follicular papules

---

## 🔗 Correlation Analysis

Several features showed strong correlations.

Some of the strongest relationships were:

| Feature 1 | Feature 2 | Correlation |
|---|---|---:|
| melanin_incontinence | vacuolisation_and_damage_of_basal_layer | 0.9417 |
| vacuolisation_and_damage_of_basal_layer | saw-tooth_appearance_of_retes | 0.9384 |
| vacuolisation_and_damage_of_basal_layer | band-like_infiltrate | 0.9376 |
| follicular_horn_plug | perifollicular_parakeratosis | 0.9289 |
| saw-tooth_appearance_of_retes | band-like_infiltrate | 0.9287 |

Correlation analysis was used to understand relationships between features and support model interpretation.

---

## 🤖 Machine Learning

The project evaluates multiple classification approaches and uses:

- Stratified train-test split
- Cross-validation
- Hyperparameter tuning
- Classification metrics
- Confusion matrix
- Feature importance
- Permutation importance
- ROC-AUC

### Train-Test Split

```text
Training Set: 292 records
Testing Set : 74 records
```

The split was stratified to preserve the class distribution.

---

## 🏆 Final Model

After model comparison, cross-validation, and hyperparameter tuning, the **Random Forest Classifier** was selected as the final model.

### Best Random Forest Parameters

```python
{
    'max_depth': None,
    'max_features': 'sqrt',
    'min_samples_leaf': 1,
    'min_samples_split': 10,
    'n_estimators': 100
}
```

### Best Cross-Validation Result

```text
Mean Accuracy    : 0.9828
Std Accuracy     : 0.0154

Mean Macro F1    : 0.9770
Std Macro F1     : 0.0223

Mean Weighted F1 : 0.9823
Std Weighted F1  : 0.0160
```

---

## 📈 Final Model Performance

The final Random Forest achieved:

| Metric | Score |
|---|---:|
| Accuracy | **97.30%** |
| Precision | **97.30%** |
| Recall | **97.30%** |
| F1 Score | **97.30%** |
| Macro F1 | **96.94%** |
| Weighted F1 | **97.30%** |

### Classification Report

| Class | Precision | Recall | F1-Score |
|---|---:|---:|---:|
| 1 | 1.00 | 1.00 | 1.00 |
| 2 | 0.92 | 0.92 | 0.92 |
| 3 | 1.00 | 1.00 | 1.00 |
| 4 | 0.90 | 0.90 | 0.90 |
| 5 | 1.00 | 1.00 | 1.00 |
| 6 | 1.00 | 1.00 | 1.00 |

---

## 📊 Confusion Matrix

The final confusion matrix was:

```text
[[23  0  0  0  0  0]
 [ 0 11  0  1  0  0]
 [ 0  0 15  0  0  0]
 [ 0  1  0  9  0  0]
 [ 0  0  0  0 10  0]
 [ 0  0  0  0  0  4]]
```

The main classification errors occurred between **Class 2 and Class 4**.

---

## ⭐ Feature Importance

The most important features in the final Random Forest included:

1. `clubbing_of_the_rete_ridges`
2. `fibrosis_of_the_papillary_dermis`
3. `thinning_of_the_suprapapillary_epidermis`
4. `spongiosis`
5. `elongation_of_the_rete_ridges`
6. `koebner_phenomenon`
7. `vacuolisation_and_damage_of_basal_layer`
8. `PNL_infiltrate`
9. `focal_hypergranulosis`
10. `band-like_infiltrate`

Permutation feature importance was also analyzed to provide an additional view of feature contribution.

---

## 📈 ROC-AUC

The final model achieved:

```text
Macro ROC-AUC    : 0.9977
Weighted ROC-AUC : 0.9978
```

### Class-wise ROC-AUC

| Class | ROC-AUC |
|---|---:|
| 1 | 1.0000 |
| 2 | 0.9892 |
| 3 | 1.0000 |
| 4 | 0.9969 |
| 5 | 1.0000 |
| 6 | 1.0000 |

---

## 🔮 Sample Prediction

A sample prediction produced:

```text
Predicted Class: 2

Class Probabilities:
Class 1: 7.93%
Class 2: 44.29%
Class 3: 1.08%
Class 4: 21.50%
Class 5: 20.54%
Class 6: 4.66%
```

The model selected **Class 2** because it had the highest predicted probability.

However, the probability was only **44.29%**, demonstrating that model predictions should be interpreted carefully.

---

## 🩺 Early Identification / Decision Support

The proposed workflow is:

```text
Patient
   ↓
Clinical Assessment
   ↓
Clinical + Histopathological Features
   ↓
Machine Learning Model
   ↓
Predicted Disease Class + Probabilities
   ↓
Further Medical Evaluation
   ↓
Doctor's Final Assessment
```

The model can potentially support early identification by providing an additional classification signal, but the final diagnosis must be made by a qualified medical professional.

---

## ⚠️ Limitations

- The dataset contains only 366 records.
- The six classes are imbalanced.
- The test set contains only 74 records.
- Eight Age values were missing in the original data.
- Several features have strong correlations.
- The model requires evaluation on an independent external dataset before real-world use.
- Clinical validation has not been established.
- The model should not independently determine diagnosis or treatment.

---

## 🛠️ Technologies Used

- **Python**
- **Pandas**
- **NumPy**
- **Matplotlib**
- **Seaborn**
- **Scikit-learn**
- **Jupyter Notebook**
- **Machine Learning**
- **Random Forest**
- **SVM**
- **Cross-Validation**
- **GridSearchCV**

---

## 📁 Suggested Project Structure

```text
Skin-Disease-Prediction/
│
├── Skin_Disease_Prediction.ipynb
├── skin_disease_random_forest_pipeline.pkl
├── Doctor_Suggestions_Early_Identification.txt
├── Limitations_and_Project_Considerations.txt
├── Challenges_Faced.txt
├── README.md
├── Data/
    └── skin_dermatology.csv
    └── skin_dermatology_clean.csv

```

---

## 🚀 How to Run the Project

### 1. Clone the repository

```bash
git clone https://github.com/DEVAM0711/Skin_Disease_Prediction.git
```

### 2. Open the project

```bash
cd Skin-Disease-Prediction
```

### 3. Install dependencies

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

### 4. Start Jupyter Notebook

```bash
jupyter notebook
```

### 5. Open the notebook

Open:

```text
Skin_Disease_Prediction.ipynb
```

Run the notebook cells from top to bottom.

---

## 💡 Key Project Takeaways

- Performed complete EDA on clinical and histopathological features.
- Handled missing Age values and validated the dataset.
- Used stratified sampling for an imbalanced multi-class dataset.
- Compared multiple machine-learning models.
- Applied cross-validation and hyperparameter tuning.
- Selected a tuned Random Forest as the final model.
- Achieved **97.30% test accuracy** and **96.94% Macro F1**.
- Achieved **0.9977 Macro ROC-AUC**.
- Analyzed feature importance and model predictions.
- Developed an early-identification decision-support workflow.

---

## ⚕️ Disclaimer

This project is for **educational and machine-learning research purposes only**. The predictions generated by the model should not be considered a medical diagnosis. Any real-world medical decision should be made by an appropriately qualified healthcare professional using appropriate clinical evidence. 

---

## 👨‍💻 Author

**Devam Jasani**

Data Science & AI/ML Engineer

---


### 👨‍💻Contributing 



* Contributions are welcome! If you have suggestions or improvements, please fork the repository and submit a pull request.

---

## ⭐ If you found this project useful, don't forget to star this repository!
