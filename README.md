# Predicting CO2 Emissions Based on Vehicle Features

Carbon dioxide (CO2) emissions from burning fossil fuels are a major cause of atmospheric changes and climate disruptions. As a result, environmental concerns are growing, and governments must provide accurate forecasts to create effective preventative policies. This report presents the findings of a project that analyzes and predicts CO2 emissions based on vehicle features using a dataset from Canada's open data portal. The study explores the relationship between various vehicle attributes, such as engine size, fuel type, and transmission type, and their impact on CO2 emissions. Statistical analysis, machine learning, and data visualization techniques are employed to identify patterns, understand the influence of these features, and develop a multiple linear regression model for predicting emissions. The results of this analysis offer valuable insights for consumers, policymakers, and automotive manufacturers to make informed decisions regarding vehicle design, regulations, and purchases.

## Dataset Overview

The dataset used in this project comes from Natural Resources Canada by the Canadian Government and offers detailed information on a range of vehicle specs and the CO2 emissions that go along with them. By using statistical analysis, machine learning, and data visualization, the study seeks to provide a solid knowledge of how these characteristics affect emissions.

The dataset spans a period of seven years and comprises 7,385 rows and 12 columns. Each row represents a unique vehicle, while each column details a specific characteristic. Key attributes include the make and model of the vehicle, which indicate the manufacturer and specific car type, respectively. The vehicle class categorizes cars based on utility, capacity, and weight, which play a role in fuel efficiency and emission levels. Engine size, measured in liters, and the number of cylinders provide insights into a vehicle’s power and efficiency. The dataset also includes details on the transmission type, such as automatic, manual, or other variants, and the number of gears.

---

## Preprocessing

A crucial stage in the data analysis process is data preprocessing, which aims to convert unstructured data into a clear, intelligible format that can be used for modeling and analysis. Initially, the dataset was loaded using the pandas library, and its structure was explored to understand the data. Managing missing values, locating and eliminating discrepancies, and making sure the data follows a consistent structure are all part of this process.

Preprocessing for this dataset started with using the `isnull().sum()` function to check for null values. This guaranteed that the data was full without the need for imputation because there were no missing entries in any of the columns.

For better readability and coding usability, long and inconsistent names were swapped out for succinct, descriptive, snake_case replacements. For instance, "Fuel Consumption City (L/100 km)" was changed to `fuel_cons_city`. The `rename()` function for specific mappings and the `skimpy` library for automated cleaning made this renaming possible. 

1,103 redundant rows were found via duplication analysis and eliminated using the `drop_duplicates()` function with `keep='first'`. This reduced the dataset size from 7,385 to 6,282 unique records. Removing duplicates is crucial to maintaining the integrity of dataset insights.

To find possible problems and compute fundamental statistics, the data was examined. For example, it was discovered that the average fuel usage for driving in cities was 13.09 L/100 km, while the average for driving on highways was much lower at 9.35 L/100 km. The average fuel economy was 25.4 mpg, and the total fuel consumption for all vehicles was 11.22 L/100 km. Furthermore, the vehicles' environmental impact was reflected in the mean CO2 emissions, which were determined to be 256.6 g/km. These findings brought to light significant variations in fuel usage trends among driving scenarios.

---

## Statistical Analysis

We conducted a number of statistical analyses in this part to gain a better understanding of the connections between various vehicle features and CO2 emissions. Several important criteria, including vehicle make, model, engine size, fuel type, and more, were the focus of our investigation. The following conclusions can be drawn from the data:

### 1.3.1 Carbon Emission Based on 'Make' (Brand of Car)

Vehicle make-based CO2 emissions investigation revealed that brand-to-brand variations in CO2 emissions are substantial. Hyundai had the lowest CO2 emissions, while Lamborghini had the highest. Emissions from brands like Smart, Honda, and Mazda were lower than the average CO2 emissions of the whole, which was about 250 g/km. This implies that fuel economy and ecologically friendly automobiles are given top priority by these manufacturers. As a result of their emphasis on high-performance engines, performance-oriented brands such as Lamborghini, Rolls-Royce, and Bugatti had emissions that were higher than normal.

### 1.3.2 Carbon Emission Based on 'Model'

Distinct CO2 emission patterns were shown by several vehicle types, which represented categories such as sports cars, SUVs, and hybrids. According to this data, a vehicle's model has a major impact on its CO2 emissions, with variables such as engine size, type, and fuel economy technology having a significant impact.

### 1.3.3 Carbon Emission Based on 'Vehicle Class'

The analysis of CO2 emissions based on vehicle class showed that vehicle size and type are key determinants of CO2 emissions. Larger vehicles, such as SUVs and trucks, tend to have higher emissions, while smaller vehicles, such as compact cars, tend to have lower emissions. This reinforces the general understanding that heavier and larger vehicles consume more fuel and emit more CO2.

### 1.3.4 Carbon Emission Based on 'Engine Size (L)'

The relationship between engine size and CO2 emissions was also explored, showing a clear positive correlation. Larger engines generally produce higher CO2 emissions. The data points were clustered in groups based on fuel type, suggesting that different fuel types exhibit different emission patterns.

---

## Prediction Model

### 1.3.10 Multiple Regression

The goal of the multiple linear regression model is to forecast the CO2 emissions of automobiles by considering a number of independent variables, including engine size, combined fuel consumption, and fuel consumption in both urban and rural settings. The objective is to use these traits to create a model that can forecast the target variable, `co2_g_km`.

We start by defining the target (`y`) as `co2_g_km` and the features (`X`) as `engine_size_l`, `fuel_cons_city`, `fuel_cons_hwy`, and `fuel_cons_comb`. After dividing the data into training and testing subsets, a straightforward linear regression model is fitted to the data, and predictions are made on the test data.

We calculate the correlation matrix and highlight features that show strong correlations to reduce multicollinearity, which can impair the model's performance. To cut down on redundancy, features with significant correlations may be removed or combined. Furthermore, regularization-based methods like Ridge and Lasso regression can assist in reducing the influence of correlated features on the model.

### 1.3.11 Polynomial Features

When there is a nonlinear relationship between the dependent and independent variables, polynomial regression might be helpful. To capture non-linear interactions, we investigate polynomial modifications of the characteristics.

### 1.3.12 Ridge and Lasso Regression

- **Ridge Regression**: This reduces the size of the coefficients to avoid overfitting by adding a penalty component proportional to the square of the coefficients.
- **Lasso Regression**: This uses an L1 penalty, promoting sparsity in the coefficients and is useful when there are many features, helping identify the most important predictors.

---

## Evaluation Matrix

Understanding how well the regression models fit the data and generate predictions depends on their evaluation. We use important measures such as R² (Coefficient of Determination), Mean Absolute Error (MAE), Mean Squared Error (MSE), and Root Mean Squared Error (RMSE) to evaluate the models' performance. Higher values indicate a better fit.

The graphs compare the performance of the model using three metrics: MSE, MAE, and R² across the training and test datasets.

- **MSE**: 441.13 (training), 466.24 (test)
- **MAE**: 13.78 (training), 14.23 (test)
- **R²**: 0.87 (both training and test sets)

The graphs and residual plots demonstrate that the model performs well on both training and test data, effectively balancing accuracy and generalization.
