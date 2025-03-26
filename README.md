# Sex Classification from Postcranial Bone Measurements

This Colab-based analysis performs statistical and machine learning evaluation of postcranial skeletal measurements to classify sex. The code:

- Loads and preprocesses left and right bone datasets
- Applies KNN and iterative imputation for missing values
- Performs Mann-Whitney U (Wilcoxon rank-sum) tests to assess sex-based differences
- Trains and evaluates classifiers (XGBoost, LightGBM, Random Forest, Logistic Regression) per bone and bone group
- Saves performance metrics, visualizes overfitting, and exports selected models and decision rules
- Supports LaTeX table generation for publication

All data paths are set to Google Drive. The notebook is intended to be run in Google Colab.
