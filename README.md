## Sportsperson injury risk prediction (baseline ml - Streamlit webb app) ##-----

This repositary consist of a simple and deployable machine learning baseline model which predicts the injury risk level as 'High risk' or 'Low risk' for training, recover and physiological indicators.

I built this as a starting benchmark project to showcase my expertise in machine learning. Moreover, the focus is: clean preprocessing, correct evaluation and a working end to end deployment.

# What the model does
When these inputs are given:
                            - age, gender, height, weight
                            - training frequency, training duration, training intensity, warmup time
                            - sleep hours, recovery time, flexibility score
                            - muscle asymmetry, injury history, stress level

The model predicts:
                   - 'Low risk' or'High risk'.
                   - probability score for high risk.

The app is deployed via streamlit so anyone can test the predictions using the web interface.


## Dataset ##

The model is trained using a public kaggle dataset in excel form. It consists of *600 samples*, *15 input features* with a binary target:  0 -->'Low risk' / 1 -->'High risk'.
The streamlit app does not ship the dataset, but loads the saved model artifacts.


## Models trained ##

I trained and compared multiple standard ML classifiers:
                                                        - Logistic regression  
                                                        - Random forest  
                                                        - Gradient boosting  
                                                        - Support Vector Machine (SVM)  
                                                        - XGBoost  

I selected the final model based on **Validation ROC-AUC**, then reported final metrics on the held-out test set.


## Evaluation  ##

The notebook includes:
                      - Accuracy/ Precision/ Recall/ F1 score
                      - ROC-AUC
                      - confusion matrix
                      - classification report

Foe the deployment, the final trained model and the preprocessing artifacts are required.


## Project structure ##

 :  -app.py
    -requirements.txt
    -artifacts :
               -- best_injury_risk_model.pkl - The chosen trained classifier.
               -- scaler.pkl                 - Standard scaler (fits only on training data)
               -- feature_columns.pkl        - Ensures the correct order of input columns. 


## How the prediction pipeline works
- User fills in the values in the streamlit user interface.
- Inputs are then converted to a single-row dataframe.
- Columns are set in order using feature_columns.pkl
- Inputs are scaled using the scaler.pkl
- Model predicts: class label(1/0) & probability of risk

## NOTES:
         - This is a baseline model trained on a small, clean and tabular dataset.
         - It is not medically accurate and should not be used for clinical descisions.
         - The goal is to show real ML practice.



## Why I built this

I'm very much fascinated in applying AI to solve real world problems and this specific idea sparked from the injuries I have personally experienced and witnessed. I wanted to explore how machine learning can detect risk signals early.

This baseline is a part of the learning progression in this area of study, after this I worked on a deeper project using PyTorch LSTM, rolling baselines, optuna tuning, and a richer time-series dataset (separate repository).


## Acknowledgements

  Dataset source: Kaggle ( https://www.kaggle.com/datasets/yuanchunhong/sirp-600-sports-injury-risk-prediction-dataset )
  Deployment : Streamlit
  Libraries : scikit-learn, XGBoost, pandas, numpy


If you want to test the model quickly, launch the app and try a few values (e.g., increase training duration + intensity with low sleep and higher stress) and observe how the risk probability changes.
 
