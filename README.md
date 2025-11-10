🎓 Campus Placement Prediction
This project focuses on predicting the placement status (Placed or Not Placed) of students based on their academic performance, demographics, and work experience. It includes data cleaning, feature encoding, model training using several popular classifiers, and a robust interactive Gradio web application for real-time predictions.

The machine learning models implemented are Logistic Regression, Random Forest Classifier, and XGBoost Classifier.

📂 Project Structure
.
├── Campus_Placement_Prediction.ipynb  # Main Jupyter Notebook
├── Placement_Data_Full_Class.csv      # The dataset (required to run the notebook)
├── placement_predictor_gradio_debug.py # (Contained within the notebook's final cell)
└── README.md                          # This file
🛠️ Setup and Requirements
To run this project, you need Python and the following libraries. The notebook is designed to run in a Jupyter or Colab environment.

Prerequisites
You can install all necessary packages using pip:

Bash
pip install numpy pandas seaborn scikit-learn xgboost gradio
Note: The Jupyter notebook includes a final cell with the entire Gradio application logic, which may rely on xgboost being installed.


The notebook provided contains code for a Campus Placement Prediction project using various machine learning classifiers, along with a full Gradio application for interactive prediction.

Here is a comprehensive README.md file for your GitHub repository.

🎓 Campus Placement Prediction
This project focuses on predicting the placement status (Placed or Not Placed) of students based on their academic performance, demographics, and work experience. It includes data cleaning, feature encoding, model training using several popular classifiers, and a robust interactive Gradio web application for real-time predictions.

The machine learning models implemented are Logistic Regression, Random Forest Classifier, and XGBoost Classifier.

📂 Project Structure
.
├── Campus_Placement_Prediction.ipynb  # Main Jupyter Notebook
├── Placement_Data_Full_Class.csv      # The dataset (required to run the notebook)
├── placement_predictor_gradio_debug.py # (Contained within the notebook's final cell)
└── README.md                          # This file
🛠️ Setup and Requirements
To run this project, you need Python and the following libraries. The notebook is designed to run in a Jupyter or Colab environment.

Prerequisites
You can install all necessary packages using pip:

Bash
pip install numpy pandas seaborn scikit-learn xgboost gradio
Note: The Jupyter notebook includes a final cell with the entire Gradio application logic, which may rely on xgboost being installed.

📊 Dataset Overview
The dataset (Placement_Data_Full_Class.csv) contains 215 records and 15 columns detailing student profiles.

Column	Description	Data Type	Missing Values (Initial)
sl_no	Serial Number	int64	0
status	Target variable: Placed (1) or Not Placed (0)	object	0
gender	Gender (M/F)	object	0
ssc_p	Secondary School Percentage	float64	0
hsc_p	Higher Secondary School Percentage	float64	0
degree_p	Degree Percentage	float64	0
mba_p	MBA Percentage	float64	0
etest_p	Employability Test Percentage	float64	0
workex	Work Experience (Yes/No)	object	0
specialisation	Specialisation in MBA (Mkt&Fin/Mkt&HR)	object	0
ssc_b, hsc_b	Board of Education (Central/Others)	object	0
hsc_s	H.S.C. Specialisation (Science/Commerce/Arts)	object	0
degree_t	Degree Type (Sci&Tech/Comm&Mgmt/Others)	object	0
salary	Salary offered (for placed candidates)	float64	67 (Missing)
🧹 Data Preprocessing Steps
The notebook performs the following key preprocessing steps:

Missing Value Imputation:

The salary column, which had 67 missing values (corresponding to 'Not Placed' students), was imputed with the median salary (265000.0) of the placed students.

Note: In the final Gradio script, the sl_no and salary columns are dropped before training the predictive models, as salary information leaks the status target.

Feature Encoding (Categorical to Numeric): All categorical columns were manually mapped to numeric values:

status: Placed → 1, Not Placed → 0

gender: M → 1, F → 0

workex: Yes → 1, No → 0

specialisation: Mkt&HR → 1, Mkt&Fin → 0

hsc_b: Central → 1, Others → 0

hsc_s: Science → 2, Commerce → 1, Arts → 0

degree_t: Sci&Tech → 2, Comm&Mgmt → 1, Others → 0

Train-Test Split: The data is split with test_size=0.2 and random_state=2 for the model training section. (The Gradio app uses random_state=42 and standard scaling).

🤖 Model Performance (Notebook Results)
The predictive model focuses on the binary classification task of predicting status. The notebook evaluates three classifiers using one-hot encoding on the train and test sets, which leads to an accuracy of 83.72% for all three models:

Model	Accuracy Score (on Test Set)	Confusion Matrix Result
Logistic Regression	83.72%	[[8, 5], [2, 28]]
Random Forest Classifier	(Prediction not shown, but trained)	
XGBoost Classifier	(Prediction not shown, but trained)	
Note on Logistic Regression Confusion Matrix ([[TN, FP], [FN, TP]]):


💻 Interactive Demo (Gradio)
The final cell of the notebook contains a comprehensive script to set up a debug-friendly interactive interface using Gradio.

This interface allows you to:

Input student features (e.g., gender, scores, specialisation).

Select one of the trained models (Logistic Regression, Random Forest, or XGBoost).

Receive a real-time Placement Prediction (Placed or Not Placed).

View a Debug / Trace log detailing how the input was processed and encoded internally.

To run the Gradio interface, simply execute the final code cell in the Campus_Placement_Prediction.ipynb notebook.
