DION SEX ESTIMATION MODELS (XGBoost, LightGBM, Random Forest)
-------------------------------------------------------------

This folder contains:

1. Pre-trained sex classification models saved as .pkl (pickle) files.
2. A sample input CSV file you can use to test the models.
3. This README file to help you understand how to use the models.

-------------------------------------------------------------
WHAT THESE MODELS DO
-------------------------------------------------------------

Each model predicts sex (0 = Female, 1 = Male) using a set of bone measurements.

The models were trained using various classifiers (XGBoost, LightGBM, and Random Forest) on the Dion dataset, which includes missing data.

- XGBoost and LightGBM models were trained using both the original data (with missing values) and imputed datasets.
- Random Forest models were only trained on KNN- or Iterative-imputed datasets, as they do not handle missing data natively.

Separate models were trained for left and right side bone measurements.

-------------------------------------------------------------
BONE GROUPS AND VARIABLES
-------------------------------------------------------------

Models were trained for the following bone groups using the specified variables:

Clavicle:
- Clavicle maximum length
- Clavicle sagittal diameter at midshaft
- Clavicle vertical diameter at midshaft

Scapula:
- Scapula height
- Scapula breadth

Humerus:
- Humerus maximum length
- Humerus epicondylar breadth
- Humerus vertical diameter of head
- Humerus maximum diameter at midshaft
- Humerus minimum diameter at midshaft

Radius:
- Radius maximum length
- Radius sagittal diameter at midshaft
- Radius transverse diameter at midshaft

Ulna:
- Ulna maximum length
- Ulna dorso-volar diameter
- Ulna transverse diameter
- Ulna physiological length
- Ulna minimum circumference

Femur:
- Femur maximum height
- Femur bicondylar length
- Femur epicondylar breadth
- Femur maximum head diameter
- Femur sagittal subtrochanteric diameter
- Femur transverse subtrochanteric diameter
- Femur sagittal midshaft diameter
- Femur transverse midshaft diameter
- Femur midshaft circumference

Tibia:
- Tibia length
- Tibia maximum proximal epiphyseal breadth
- Tibia maximum distal epiphyseal breadth
- Tibia maximum diameter at the nutrient foramen
- Tibia transverse diameter at the nutrient foramen
- Tibia circumference at the nutrient foramen

Fibula:
- Fibula maximum length
- Fibula maximum diameter at midshaft

Calcaneus:
- Calcaneus maximum length
- Calcaneus middle breadth

-------------------------------------------------------------
MODEL FILE NAMING CONVENTION
-------------------------------------------------------------

Each model file is named like this:

    ModelType_BoneGroup_ImputationSide.pkl

Example:
    XGBoost_Humerus_KNN_L.pkl

This means:
- Model: XGBoost
- Bone Group: Humerus
- Dataset: KNN-imputed
- Side: Left

-------------------------------------------------------------
SAMPLE INPUT FORMAT (CSV)
-------------------------------------------------------------

We’ve included a file: sample_data_for_prediction.csv

It contains two example individuals with Humerus measurements:

Humerus maximum length,Humerus epicondylar breadth,Humerus vertical diameter of head,Humerus maximum diameter at midshaft,Humerus minimum diameter at midshaft  
310.0,66.2,43.1,23.0,20.1  
280.5,58.3,39.8,20.7,18.9  

To use your own data:
- Replace the values with your own measurements
- Ensure the column names match exactly
- You can include multiple rows (one per individual)

For other models (e.g., Clavicle, Scapula, Femur, etc.), construct similar CSV files using the variable lists above.

Important:
- Random Forest models require all variables to be present (no missing values)
- Boosting models (XGBoost, LightGBM) can work even if some variables are missing

-------------------------------------------------------------
HOW TO RUN A MODEL ON YOUR DATA
-------------------------------------------------------------

In Python:

1. Install required libraries (if needed):

    pip install joblib pandas scikit-learn xgboost lightgbm

2. Load your CSV and a model:

import pandas as pd  
import joblib  

# Load your data  
df = pd.read_csv("sample_data_for_prediction.csv")  

# Load a model  
model = joblib.load("XGBoost_Humerus_KNN_L.pkl")  

# Predict  
predictions = model.predict(df)  

# Print results  
print(predictions)  # Output: 0 = Female, 1 = Male

-------------------------------------------------------------
NOTES
-------------------------------------------------------------

- Column names must exactly match those used during training.
- Random Forest models require complete data.
- XGBoost and LightGBM models can handle missing values.

-------------------------------------------------------------
QUESTIONS?

Contact the repository maintainers or open an issue on GitHub.  
You can also reach me at: cconsta1@alumni.nd.edu
