DION LOGISTIC REGRESSION SEX ESTIMATION MODELS
----------------------------------------------

This folder contains human-readable Logistic Regression models trained to estimate biological sex (0 = Female, 1 = Male) based on postcranial bone measurements.

Each model is saved as a `.txt` file and includes information about:
- The dataset used to train the logistic regression model (KNN- or Iterative-imputed, left or right side)
- The bone group
- The coefficients for each variable belonging to the bone group
- A ready-to-use formula for score computation
- A classification rule (Score > 0 → Male, Score ≤ 0 → Female)
- An example for plugging in your own data

----------------------------------------------
HOW THESE MODELS WERE TRAINED
----------------------------------------------

The models were trained on the Dion datasets (Right and Left) using only imputed data
constructed from the original dataset. The datasets used were:

- KNN_L: K-nearest neighbor imputation (left side)
- KNN_R: K-nearest neighbor imputation (right side)
- Iterative_L: Iterative imputation (left side)
- Iterative_R: Iterative imputation (right side)

Each model was trained **separately** for each bone group and dataset variant.

----------------------------------------------
BONE GROUPS & MEASUREMENTS
----------------------------------------------

The models were trained on the following bone groups and corresponding measurements:

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
- Femur maximum heigth
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

----------------------------------------------
HOW TO USE A MODEL FILE
----------------------------------------------

Open any `.txt` file (e.g. `LogisticRegression_Humerus_KNN_R.txt`) to see:

- The model’s coefficients
- A clear formula, such as:

  Score = -79.481 + 0.087 × Humerus maximum length + 0.227 × Humerus epicondylar breadth + ...

- A classification rule:

  If Score > 0 → Classify as Male  
  If Score ≤ 0 → Classify as Female

You can compute the score using a calculator, Excel, Python, or any software. Just insert your own bone measurements into the formula.

----------------------------------------------
EXAMPLE (from Humerus model, KNN_R)
----------------------------------------------

If your measurements are (for the right side of the skeleton):

- Humerus maximum length = 300
- Humerus epicondylar breadth = 62
- Humerus vertical diameter of head = 41
- Humerus maximum diameter at midshaft = 21
- Humerus minimum diameter at midshaft = 18

And the model text gives:

Score = -79.481 + 0.087 × Humerus maximum length + 0.227 × Humerus epicondylar breadth + 0.836 × Humerus vertical diameter of head + (-0.014 × Humerus maximum diameter at midshaft) + 0.138 × Humerus minimum diameter at midshaft

Then the score would be:

Score = -79.481 + (0.087 × 300) + (0.227 × 62) + (0.836 × 41) + (-0.014 × 21) + (0.138 × 18)

Calculate the result and apply:

- If Score > 0 → Male
- If Score ≤ 0 → Female

----------------------------------------------
NOTES
----------------------------------------------

- These models are fully interpretable and can be used manually or in software.
- Input variable names must match exactly.
- Imputation method and side (left/right) must match your data for best results.

----------------------------------------------
QUESTIONS?

Contact the repository maintainers or open an issue on GitHub.  
You can also reach me at: cconsta1@alumni.nd.edu
