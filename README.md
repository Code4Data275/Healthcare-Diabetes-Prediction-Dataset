# 🩺 Diabetes Prediction Project

## 📌 Project Overview
This project predicts whether a person is **Diabetic or Non-Diabetic** based on key health features.  
We experimented with **Logistic Regression** first and then built a **Random Forest Classifier** for higher accuracy and robustness.

---

## 🧩 Dataset Details
- **Source:** Kaggle Dataset
- **Size:** 2768 samples  
- **Top Features Used:**
  1. **Glucose** 🍭  
  2. **BMI** ⚖️  
  3. **Age** 👵👴  
  4. **DiabetesPedigreeFunction** 🧬  
  5. **Pregnancies** 🤰
  6. **SkinThickness** 🧴
  7. **Insulin** 💉
  8. **BloodPressure** 🩸

- **Class Distribution:**  
  - Non-Diabetic: 65%  
  - Diabetic: 35%  
> ⚠️ Dataset slightly imbalanced → handled with class weighting and Random Forest.

---

## 🔹 Logistic Regression (Initial Attempt)
- Tried **Logistic Regression** first as a baseline model  
- **Hyperparameters tuned** using GridSearchCV:
  1. `penalty`: ['l1','l2']
  2. `C`: [0.01, 0.1, 1, 10, 100]
  3. `solver`: ['liblinear', 'saga']  

**Performance Metrics:**

| Class | Precision | Recall | F1-score | Support |
|-------|-----------|--------|----------|---------|
| 0     | 0.85      | 0.78   | 0.81     | 363     |
| 1     | 0.64      | 0.74   | 0.69     | 191     |
| **Accuracy** | — | — | 0.76     | 554     |

**Observations:**  
- Non-Diabetic class predicted well ✅  
- Diabetic class (minority) had lower precision ⚠️  
- Decided to use **Random Forest** for better handling of class imbalance and higher overall accuracy  

---

## 🛠 Random Forest Classifier

### 1️⃣ Feature Selection
- Based on feature importance from RF, skipped low-importance features:
  - Removed: Insulin, SkinThickness, BloodPressure  
  - Kept: Glucose, BMI, Age, DiabetesPedigreeFunction, Pregnancies ✅

### 2️⃣ Train-Test Split
- Stratified split to maintain class balance  
- Train:Test = 70:30  

### 3️⃣ Model Training & Hyperparameter Tuning
- Used GridSearchCV to tune:
  - n_estimators, max_depth, min_samples_split, min_samples_leaf, max_features, class_weight
- `Accuracy` used as a scoring metric

### 4️⃣ Model Evaluation
Confusion matrix:
| Actual/Predicted | Non-Diabetic (0) | Diabetic (1) |
|-------|-----------|--------|
| Non-Diabetic (0) | 537 | 8 |
| Diabetic (1) | 7 | 277 |

Classification metric:
| Class | Precision | Recall | F1-score |
|-------|-----------|--------|----------|
| 0     | 0.98     | 0.99  | 0.98    | 
| 1     | 0.97     | 0.97  | 0.97     |
| **Accuracy** | — | — | 0.98    |

Cross-validation score: 0.99
✅ Model generalizes well and predicts both classes accurately.

### 5️⃣ Feature Importance (Top 5)
| Feature | Importance |
|--------|----------|
| Glucose |	0.3299 🍭 |
| BMI |	0.2297 ⚖️ |
| Age	| 0.1837 👵👴 |
| DiabetesPedigreeFunction |	0.1526 🧬 |
| Pregnancies | 0.1041 🤰 |
- Glucose and BMI are the most influential features
- Low-importance features were removed → model simpler and cleaner

## 🚀 Next Steps / Deployment
1. Deploy as web or mobile app
2. Predict new patient data (top 5 features)
3. Optionally adjust probability thresholds for higher recall of diabetic class
4. Explain predictions using SHAP/LIME for transparency

## ⚡ Summary
1. Logistic Regression: baseline, Accuracy = 0.76
2. Random Forest: final model, Accuracy = 0.98, CV = 0.99
3. Top 5 features identified and visualized
4. Model saved and ready for deployment

## 👨‍💻 Author
**Aldous Dsouza**  
- BSc Computer Science Graduate  
- Interested in Data Science, Machine Learning, and Software Development    

