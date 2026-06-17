# Heart Disease Classifier

Trains and compares four ML models on clinical patient data to predict heart disease risk, then serves the best-performing model through a Flask web app where you can input custom values and get a live prediction.

The focus here was on interpretability alongside accuracy — in healthcare contexts, a model you can't explain isn't actually useful.

---

## Models Trained

| Model | Notes |
|---|---|
| Logistic Regression | Baseline linear model |
| Support Vector Machine | RBF kernel, good for non-linear boundaries |
| Gradient Boosting Classifier | Ensemble, strong on tabular data |
| Random Forest Classifier | Best performer; used in the web app |

All four are trained, evaluated, and saved as `.pkl` files. Metrics printed for each: accuracy, classification report, and confusion matrix.

---

## Tech Stack

- **Python** — model training and Flask backend
- **Scikit-learn** — all four classifiers, pipelines, preprocessing
- **Pandas** — data loading and manipulation
- **Flask** — web app for live predictions
- **Joblib** — model serialization

---

## Project Structure

```
HeartDiseaseClassifier/
├── model.py          # Trains all four models, prints metrics, saves .pkl files
├── app.py            # Flask app, loads Random Forest model, serves predictions
├── templates/
│   ├── index.html    # Input form (age, sex, cholesterol, etc.)
│   └── answer.html   # Displays prediction result
└── .gitignore        # Excludes .pkl and .csv files
```

---

## Getting Started

### Prerequisites
```bash
pip install flask scikit-learn pandas joblib
```

### Step 1 — Train the models
```bash
python model.py
```
This trains all four classifiers on the dataset, prints accuracy and metrics for each, and saves `.pkl` files locally.

### Step 2 — Run the web app
```bash
python app.py
```
Open the port shown in your terminal (default: `http://localhost:5000`). Fill in the patient data form and get a heart disease risk prediction from the Random Forest model.

---

## Input Features

The model takes 11 clinical features as input:

| Feature | Description |
|---|---|
| Age | Patient age in years |
| Sex | M / F |
| ChestPainType | TA, ATA, NAP, or ASY |
| RestingBP | Resting blood pressure (mm Hg) |
| Cholesterol | Serum cholesterol (mg/dl) |
| FastingBS | Fasting blood sugar > 120 mg/dl (1 = true) |
| RestingECG | Normal, ST, or LVH |
| MaxHR | Maximum heart rate achieved |
| ExerciseAngina | Exercise-induced angina (Y / N) |
| OldPeak | ST depression induced by exercise |
| ST_Slope | Up, Flat, or Down |
