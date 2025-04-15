Smart Water Monitoring - Machine Learning Challenge - Hackerearth
-----------------------------------------------------------------
Author: Sreenija Earanki

Objective:
----------
To build a machine learning model that predicts daily water consumption per household using a variety of features such as household demographics, weather conditions, and behavioral patterns.

Dataset Summary:
----------------
- train.csv (14,000 rows): Contains historical water consumption data along with 11 features.
- test.csv (6,000 rows): Same features (except target).
- sample_submission.csv: Shows the expected format of the final predictions.

Target variable:
----------------
- Water_Consumption (float): Represents the total water consumed for a given 8-hour period.

Approach:
---------
1. Exploratory Data Analysis & Cleaning
   - Converted 'Timestamp' into datetime and extracted useful temporal features: `Hour`, `DayOfWeek`, `Month`.
   - Identified and handled missing values using appropriate imputation:
     - Categorical features (`Amenities`, `Apartment_Type`, `Income_Level`) filled with `'Unknown'` or mode.
     - Numeric features (`Humidity`, `Temperature`, `Appliance_Usage`) filled using median imputation.
   - Removed the original `Timestamp` column after extracting time features.

2. Feature Engineering
   - Extracted time-based features: `Hour`, `DayOfWeek`, and `Month` to capture daily and weekly patterns.
   - Applied **Label Encoding** to categorical features (`Apartment_Type`, `Income_Level`, `Amenities`) for compatibility with tree-based models.

3. Model Selection
   - Chose **Random Forest Regressor** as the baseline model due to its robustness, ability to handle nonlinear relationships, and resilience to outliers and multicollinearity.
   - Random Forest is particularly effective on tabular data and handles mixed data types (categorical + numerical) well after encoding.

4. Training & Validation
   - Split the training data (80/20) to evaluate model performance.
   - Used **Root Mean Squared Error (RMSE)** as the evaluation metric, consistent with the competition's custom scoring formula.
   - Achieved reasonable performance on validation set with limited hyperparameter tuning.

5. Prediction
   - Trained final model on the entire training dataset.
   - Generated predictions on the test set.
   - Constructed a submission file with predicted `Water_Consumption` values aligned with the correct `Timestamp` entries.

Tools & Libraries:
------------------
- Python 3.x
- pandas, numpy: Data manipulation and preprocessing
- scikit-learn: Model building and evaluation
  - RandomForestRegressor
  - LabelEncoder
  - train_test_split
- zipfile: For packaging submission files

Future Scope:
-------------
- Try more powerful models like XGBoost or LightGBM.
- Hyperparameter tuning using GridSearchCV or RandomizedSearchCV.
- Investigate temporal trends further with time series analysis techniques.
- Explore SHAP or permutation feature importance to interpret model behavior.

Submission Files:
-----------------
- submission.csv (prediction file)
- explanation.txt (this file)
- water.ipynb (source code)
