# SpaceX Falcon 9 Predictive Model

## Background

SpaceX, a pioneering force in the space industry, aims to make space travel accessible to all. Notable achievements include sending spacecraft to the International Space Station, launching a satellite constellation for global internet access, and conducting manned missions. SpaceX's cost-effective launches ($62 million per launch) result from the innovative reuse of the first stage of its Falcon 9 rocket, a strategy that significantly reduces costs compared to providers unable to reuse the first stage (costing upwards of $165 million each). Predicting the success of the first stage landing is crucial in determining the launch price. This project utilizes public data and machine learning models to predict whether SpaceX or a competing company can successfully reuse the first stage.

## Objectives

- Explore how payload mass, launch site, number of flights, and orbits impact first-stage landing success.
- Analyze the rate of successful landings over time.
- Determine the best predictive model for successful landings (binary classification).

## Executive Summary

This research aims to identify factors influencing successful rocket landings. The following methodologies were employed:

1. **Data Collection - API:**
   - Requested data from SpaceX API (rocket launch data).
   - Decoded responses using `.json()` and converted to a dataframe using `.json_normalize()`.
   - Requested information about launches using custom functions.
   - Created a dictionary and dataframe from the data.
   - Filtered the dataframe to contain only Falcon 9 launches.
   - Replaced missing values of Payload Mass with calculated `.mean()`.
   - Exported data to a CSV file.

2. **Data Collection - Web Scraping:**
   - Requested data (Falcon 9 launch data) from Wikipedia.
   - Created a BeautifulSoup object from HTML responses.
   - Extracted column names from HTML table headers.
   - Collected data by parsing HTML tables.
   - Created a dictionary and dataframe from the data.
   - Exported data to a CSV file.

3. **Data Wrangling:**
   - Converted outcomes into 1 for a successful landing and 0 for an unsuccessful landing.

4. **Exploratory Data Analysis (EDA) with Visualization:**
   - Created charts to analyze relationships and show comparisons.

5. **EDA with SQL:**
   - Queried the data to gain deeper insights.

6. **Maps with Folium:**
   - Created maps to visualize launch sites, view launch outcomes, and assess proximity to geographical markers.

7. **Dashboard with Plotly Dash:**
   - Created a dashboard with interactive elements.
   - Included a pie chart showing successful launches and a scatter chart showing Payload Mass vs. Success Rate by Booster Version.

8. **Predictive Analytics:**
   - Created a NumPy array from the Class column.
   - Standardized the data with StandardScaler.
   - Split the data using train_test_split.
   - Created a GridSearchCV object with cv=10 for parameter optimization.
   - Applied GridSearchCV on different algorithms: logistic regression, support vector machine (SVC), decision tree, and K-Nearest Neighbor (KNN).
   - Calculated accuracy on the test data using `.score()` for all models.
   - Assessed the confusion matrix for all models.
   - Identified the best model using Jaccard Score, F1 Score, and Accuracy.

## Results

### Exploratory Data Analysis (EDA):

- Launch success has improved over time.
- KSC LC-39A has the highest success rate among landing sites.
- Orbits ES-L1, GEO, HEO, and SSO have a 100% success rate.

### Visualization / Analytics:

- Most launch sites are near the equator, and all are close to the coast.

### Predictive Analytics:

- All models performed similarly on the test set. The decision tree model slightly outperformed when looking at `.best_score_`.

## Conclusion

### Research Findings:

- Model Performance: The models performed similarly on the test set, with the decision tree model slightly outperforming.
- Equator Advantage: Most launch sites are near the equator, providing an additional natural boost due to the Earth's rotational speed, reducing fuel and booster costs.
- Coastal Proximity: All launch sites are close to the coast.
- Launch Success Trend: Success rates increase over time.
- KSC LC-39A: Has the highest success rate among launch sites. Achieves a 100% success rate for launches less than 5,500 kg.
- Orbits: ES-L1, GEO, HEO, and SSO have a 100% success rate.
- Payload Mass: Across all launch sites, the higher the payload mass (kg), the higher the success rate.

### Additional Considerations:

- Dataset: A larger dataset will help build on predictive analytics results to understand if findings can be generalized to a larger dataset.
- Feature Analysis / PCA: Additional feature analysis or principal component analysis should be conducted to see if it can help improve accuracy.
- XGBoost: A powerful model not utilized in this study. It would be interesting to see if it outperforms other classification models.
