## Personalized Healthcare Prediction 

<img width="2048" height="1249" alt="health" src="https://github.com/user-attachments/assets/17476669-0107-49b7-a356-9ca38c8d478a" />



 
This repository contains a hands-on machine learning project that predicts the likelihood of a donor giving blood in the future and generates simple, human-readable recommendations for donor engagement. The workflow lives in a single Jupyter notebook: Healthcare_Predictions.ipynb.
 
## Project Highlights

Problem: Binary classification — predict whether a donor will donate in the future (Class).
Data: blood.csv (commonly known as the Blood Transfusion Service Center dataset).
Features (typical for this dataset):
Recency: Months since last donation
Frequency: Total number of donations
Monetary: Total volume donated (c.c.)
Time: Months since first donation
Target: Class (1 = donated, 0 = not donated)
Modeling: Pipeline with preprocessing and a RandomForestClassifier
Evaluation: classification_report, confusion_matrix
Explainability/EDA: Correlation heatmap, class distribution plots, boxplots by recommendation
Personalization: Generates simple text recommendations based on the predicted class

 If your blood.csv has different column names, update the notebook sections that reference them.

## Repository Structure 
├── Healthcare_Predictions.ipynb          # Main end‑to‑end workflow
├── blood.csv                             # Dataset (not included in repo by default)
└── README.md                             # You are here


## Environment Setup

Python: 3.9+ (works with newer versions too)
Key libraries:
pandas, numpy
scikit-learn
matplotlib, seaborn


## How to Run

Place blood.csv at the root of the project (or adjust the file path in the notebook).
Open the notebook:
jupyter notebook Healthcare_Predictions.ipynb
Run all cells, top to bottom.
If you prefer VS Code, open the notebook, select a Python kernel, and Run All.

## What the Notebook Does (Step-by-Step)

1. Load Data

2. Reads blood.csv into a pandas DataFrame.

3. Quick sanity checks with .head(), .describe(), and dtypes.

4. Define Features & Target

         X = data.drop('Class', axis=1)

        y = data['Class']

5. Train/Test Split
                      train_test_split(X, y, test_size=0.2, random_state=42)

6. Preprocessing + Model in a Pipeline

Since features are numeric, applies StandardScaler (if configured) and a RandomForestClassifier via sklearn.pipeline.Pipeline.
You can easily swap the estimator (e.g., LogisticRegression, XGBClassifier).

7. Model Training

Fits the pipeline on X_train, y_train.

8. Evaluation

classification_report(y_test, y_pred) — precision, recall, f1-score, and support.
confusion_matrix(y_test, y_pred) — inspect false positives/negatives.

9. Personalized Recommendations

Appends predicted class to the test set.

10. 
  Maps predictions to simple strategies:
Predicted 1 (Likely Donor) → “Encourage regular donation. Consider rewarding loyalty.”
Predicted 0 (Unlikely Donor) → “Re-engage with reminders, health tips, and community impact stories.”

 Produces visuals like:
Recommendation distribution pie chart
Boxplot of Recency by Recommendation
Correlation heatmap (including predicted/actual where available)


## Data Source & Credits

This project uses the Blood Transfusion Service Center dataset (commonly mirrored across ML repositories). If you publish the dataset, include proper attribution and license. If your blood.csv comes from elsewhere, update this section with the correct citation.

