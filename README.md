# What Drives the Price of a Car?

## Summary

In this exercise, I will explore a dataset from Kaggle. I analyzed a large dataset of used cars to uncover the most important factors that drive car prices. 
I used advanced modeling techniques to analyze and predict car prices based on features like age, mileage, make, condition, and more.
By understanding these patterns, a used-car dealership can make smarter decisions when sourcing, pricing, and marketing inventory.

## Link To The Jupyter Notebook

[use_car_price_prediction](use_car_price_prediction.ipynb)

## CRISP-DM Process

### Business Understanding

To support the used car dealership in understanding price determinants, we will approach this as a supervised regression problem. Using historical data on used car sales, including features such as make, model, year, mileage, transmission type, and fuel type, we aim to train a predictive model that estimates the price of a vehicle. 
Additionally, we will perform feature importance analysis to identify which variables most significantly influence price, thereby providing actionable insights for the dealership’s pricing and inventory strategy.

### Data Understanding

1. load and inspect data
2. check for missing values
3. explore feature distributions
4. identify outliers and anomalies
5. check for duplicates
6. understand relationships

### Data Preparation

1. Data cleaning: 
    1. Handling missing values
    2. Identifying and treating outliers
    3. Correcting inconsistent or erroneous data
    4. Handling noisy data
2. Data Selection 

### Modeling

build a number of different regression models with the price as the target.  In building different models, we should explore different parameters and be sure to cross-validate your findings.

* Linear
    * Linear
    * Ridge
    * Lasso
* Poly with degree of 2
    * Ridge
    * Lasso

### Evaluation

📈 Model Performance Comparison (CV MSE):

|Model Type |	Polynomial Features |	CV MSE |
| :---------------- | :------: | ----: |
|Linear Regression |	❌	|73,308K|
|Ridge Regression	|❌	|117,675K|
|Lasso Regression|	❌	|68,232K|
|Ridge Regression|	✅ Degree=2|	55,783K|
|Lasso Regression|	✅ Degree=2|		62,389K|	
|Ridge Regression|	✅ Degree=3|	55,783K|

#### Insights from Comparison:
Polynomial Ridge Regression (degree=2) has the lowest MSE, suggesting it best captures nonlinear relationships in the data.

Lasso performs reasonably well with and without polynomial features — and has the added benefit of performing feature selection by shrinking some coefficients to zero.

Plain Ridge without poly features performs poorly, possibly due to underfitting or inability to capture complex patterns.

Overall, using polynomial features leads to significantly improved performance → likely because car pricing is influenced by nonlinear interactions (e.g., age * mileage).

## Conclusion

### Key Insights

* Car Age & Mileage Are Key Drivers
    * Newer vehicles and those with lower odometer readings consistently command higher prices.
    * These two factors have a nonlinear effect—meaning the price doesn’t drop at a constant rate. For example, the first 50,000 miles reduce value more sharply than later mileage.
* Condition & Title Status Matter
    * Cars listed as "excellent" or "good" condition are valued higher than "fair" or "salvage" condition.
    * A clean title also significantly boosts a car’s resale value.
* Certain Brands Hold Value Better
    * Manufacturers like Toyota and Honda tend to retain value better over time compared to other makes.
    * Dealers may consider prioritizing brands with historically strong resale performance.

### Modeling Results
We tested several price prediction models, including:

|Model|	Method|	Prediction Accuracy (Lower = Better)|
| :---------------- | :------ | :---- |
|Linear Regression|	Basic Pricing Model|	Moderate|
|Lasso Regression|	Regularized Model|	Improved|
|Ridge Regression + Poly|	Advanced Model|	✅ Best Performance|

## Recommendations for Your Dealership

1. Prioritize Inventory with Low Mileage and Newer Years
    * These are the strongest predictors of higher price.
2. Target High-Retention Brands
    * Focus on acquiring and marketing cars from brands with proven resale value.
3. Maintain Car Condition
    * Small investments in cosmetic or mechanical improvements may yield strong returns.
4. Use Predictive Models for Valuation
    * Incorporate automated tools that use data modeling to support price setting and reduce human error.

## Next Steps
* Use my model to guide future purchase and pricing decisions.
* Consider building a web-based tool that estimates car value based on inputs.
* Explore additional data to further fine-tune predictions.