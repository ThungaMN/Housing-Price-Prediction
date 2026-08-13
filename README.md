# 🏠 Housing Price Prediction

## 📌 Project Overview

This project focuses on predicting house prices using Machine Learning regression techniques.

The project uses property-related information such as property age, total rooms, total bedrooms, neighborhood population, income level, and other available features to predict the `TargetPrice` of a property.

Different regression algorithms were trained and compared, including **Random Forest Regressor, Gradient Boosting Regressor, and XGBoost Regressor**.

The best-performing XGBoost model was further optimized using **RandomizedSearchCV** and used to generate predictions for the test dataset.



## 🎯 Objective

The main objectives of this project are:

* Understand and analyze housing/property data.
* Identify and handle missing values.
* Perform exploratory data analysis.
* Create meaningful features from the available data.
* Train multiple regression models.
* Compare model performance using RMSE.
* Perform cross-validation.
* Tune the XGBoost model using RandomizedSearchCV.
* Generate house price predictions for the test dataset.
* Create a `submission.csv` file containing the final predictions.



## 🛠️ Technologies Used

* Python
* Pandas – Data manipulation and analysis
* NumPy – Numerical computations
* Matplotlib – Data visualization
* Seaborn – Statistical visualization
* Scikit-learn – Machine Learning
* Random Forest Regressor
* Gradient Boosting Regressor
* XGBoost Regressor
* RandomizedSearchCV – Hyperparameter tuning
* K-Fold Cross-Validation
* Kaggle Notebook– Development environment



## 📂 Dataset

The project uses two datasets:

* `estate_train.csv` – Training dataset containing property features and the target price.
* `estate_test.csv` – Test dataset used to generate final predictions.

### Target Variable
TargetPrice


## Identifier
PropertyID


`PropertyID` is used to identify properties but is not used as a feature for model training.



## 🔍 Data Preprocessing

## 1. Missing Value Analysis

Missing values were analyzed using:

* `isnull().sum()`
* Missing-value heatmap

The `PropertyAge` column contained missing values.

## 2. Missing Value Imputation

Missing values in `PropertyAge` were replaced using the **median property age calculated from the training data**.

The same median value was applied to both training and test datasets.


## 📊 Exploratory Data Analysis

Several visualizations were performed to understand the dataset and relationships between variables.

## Visualizations included:

* Missing-value heatmap
* Target price distribution
* Correlation heatmap
* Income level vs target price scatter plot

These visualizations helped understand:

* Distribution of property prices
* Relationships between numerical features
* Missing-value patterns
* Relationship between income level and property price


## ⚙️ Feature Engineering

Additional features were created to provide the models with more useful information.

## Rooms Per Person

RoomsPerPerson = TotalRooms / (NeighborhoodPop + 1)

## Bedrooms Per Person

BedroomsPerPerson = TotalBedrooms / (NeighborhoodPop + 1)


## Income Per Room

IncomePerRoom = IncomeLevel / (TotalRooms + 1)

These features were created for both the training and test datasets.

The `+1` prevents division-by-zero errors.


## 📋 Feature Selection

The following columns were removed before model training:
PropertyID
TargetPrice


`TargetPrice` was used as the target variable, while `PropertyID` was treated as an identifier.

The remaining columns were used as input features.


## ✂️ Train-Validation Split

The training dataset was divided into:

* 80% Training Data
* 20% Validation Data

A `random_state` of `42` was used to ensure reproducibility.



## 🤖 Machine Learning Models

Three regression algorithms were trained and evaluated.

### 1. Random Forest Regressor

Random Forest combines multiple decision trees to make predictions and is useful for capturing non-linear relationships in the data.

### 2. Gradient Boosting Regressor

Gradient Boosting builds models sequentially, where each new model attempts to improve the errors made by previous models.

### 3. XGBoost Regressor

XGBoost is a powerful gradient boosting algorithm designed for high predictive performance and efficient training.

The model was configured using:


objective = reg:squarederror
random_state = 42



## 📏 Model Evaluation

The primary evaluation metric used in this project is:

### RMSE — Root Mean Squared Error

RMSE measures the average magnitude of prediction errors.

A lower RMSE indicates better model performance.

The formula is:

RMSE = √(Mean Squared Error)


The models were evaluated using validation RMSE.


## 🔄 Cross-Validation

5-fold cross-validation was used to compare the performance of:

* Random Forest
* Gradient Boosting
* XGBoost

The cross-validation score was calculated using negative mean squared error and converted into RMSE.

This provides a more reliable estimate of model performance across different subsets of the data.


## ⚙️ XGBoost Hyperparameter Tuning

`RandomizedSearchCV` was used to optimize the XGBoost model.

The following hyperparameters were explored:

* `n_estimators`
* `max_depth`
* `learning_rate`
* `subsample`
* `colsample_bytree`
* `min_child_weight`
* `gamma`

The search was configured with:


n_iter = 25
cv = 5
random_state = 42
scoring = neg_root_mean_squared_error

The best combination of hyperparameters was selected based on cross-validation RMSE.



## 🏆 Final Model

The best XGBoost estimator obtained from `RandomizedSearchCV` was used as the final model.

The optimized model was trained on the training data and evaluated on the validation dataset.

The final validation RMSE was calculated using:
python
mean_squared_error(
    y_valid,
    y_pred
)


and converted to RMSE.

### Final Validation RMSE

Validation RMSE:0.45


## 📈 Model Comparison

The project compares the performance of:

| Model                       | Evaluation      |
| --------------------------- | --------------- |
| Random Forest Regressor     | RMSE            |
| Gradient Boosting Regressor | RMSE            |
| XGBoost Regressor           | RMSE            |
| Tuned XGBoost               | Validation RMSE |

The model with the **lowest RMSE** is considered the best-performing model.


## 📝 Prediction and Submission

The optimized XGBoost model was used to predict prices for the test dataset.

The predictions were combined with the corresponding `PropertyID` values.

A file named:

submission.csv


was created with the following columns:

| Column        | Description                |
| ------------- | -------------------------- |
| PropertyID  | Unique property identifier |
| TargetPrice | Predicted property price   |




## 📌 Key Learning Outcomes

Through this project, I worked with:

* Data cleaning
* Missing-value treatment
* Exploratory Data Analysis
* Feature engineering
* Regression algorithms
* Random Forest
* Gradient Boosting
* XGBoost
* Train-validation split
* K-Fold Cross-Validation
* RandomizedSearchCV
* Hyperparameter tuning
* RMSE evaluation
* Test-set prediction
* Kaggle submission workflow


## 🔮 Future Improvements

The project can be further improved by:

* Performing more extensive feature engineering.
* Trying additional regression algorithms.
* Applying feature selection techniques.
* Performing more extensive XGBoost hyperparameter tuning.
* Comparing additional evaluation metrics such as MAE and R².
* Using ensemble or stacking techniques.
* Analyzing feature importance to identify the most influential factors affecting property prices.

---

## 👩‍💻 Author

**Thunga M N**

This project was developed as part of my learning and practice in **Data Science and Machine Learning**.
