
# The Analysis

Each Jupyter notebook in this project focused on exploring a specific aspect of the EV adoption landscape. Here's how I tackled each question:


## 1. How has electric vehicle (EV) adoption evolved in Washington State by model year, make, and vehicle type?

To explore trends in electric vehicle (EV) adoption in Washington State, I analyzed vehicle registration data from model years 2002 to 2025, focusing on the growth of specific vehicle types, including Battery Electric Vehicles (BEVs) vs Plug-in Hybrid Electric Vehicles (PHEVs). This analysis highlights shifts in consumer preferences and the evolving market dominance of these vehicle types over time.

[View the Jupyter Notebook with detailed steps here](1_Car_Trend.ipynb) 


### Visualize the Data

```python
# Group by year and vehicle type
ev_trends = df.groupby(['Model Year', 'Electric Vehicle Type'])['VIN (1-10)'].count().unstack()
ev_trends.plot(kind='line', title='EV Adoption by Type (2002-2025)', figsize=(10, 6))
plt.ylabel('Number of Vehicles Registered')
plt.show()
```
### Results

![Likelihood of Skills Requested in the US Job Postings](/images/ev_adoption_washington_3.png)

*Line graph tracking EV registrations in Washington State (2002–2025)*

### Insights:
-Battery Electric Vehicles (BEVs) have seen the most significant growth in adoption, with a dramatic spike in registrations between 2021 and 2024, peaking at over 50,000 vehicles in 2023.
Further analysis shows that BEV registrations began to rise after 2015, largely driven by the 2017 launch of the Tesla Model 3.

-BEV adoption began accelerating earlier and more rapidly than PHEVs, suggesting a stronger consumer shift toward fully electric models rather than hybrids in Washington State.

-Plug-in Hybrid Electric Vehicles (PHEVs), while growing steadily, have consistently trailed BEVs, with their highest adoption reaching just over 10,000 in 2024.

## 2. What’s the geographic distribution of EVs across counties, and how does electric range vary by make?

To gain insights into electric vehicle (EV) adoption across Washington State, we analyzed county-level registration data in conjunction with the average electric range by vehicle make. This approach sheds light on areas with the highest concentration of EVs and identifies the manufacturers providing vehicles with the longest driving range.

[View the Jupyter Notebook with detailed steps here](2_Car_Distribution.ipynb) 


### Visualize the Data

```python
# Plot styled choropleth with a more compact figure size
fig, ax = plt.subplots(figsize=(8, 5))  # Reduced size for a more compact plot
geo_df.boundary.plot(ax=ax, linewidth=1.2, color='gray')  # Clear outlines for boundaries
geo_df.plot(column='EV Count',
            cmap='Greens',
            legend=True,
            linewidth=0.5,
            edgecolor='black',
            ax=ax)

# Add styling
ax.set_title('EV Distribution Across Washington Counties', fontsize=16)
ax.axis('off')
```
### Results

![EV Distribution Across Washington Counties](/images/ev_distribution_washington_state.png)
*Electric Vehicle (EV) Ownership by County in Washington State*

### Insights:
-King County dominates EV registrations by a wide margin, with nearly 120,000 EVs, which is more than 3x the count in the next-highest county, Snohomish. This suggests a strong urban influence and infrastructure readiness in the Seattle metropolitan area.

-The choropleth map confirms a stark concentration of EVs in the Puget Sound region, particularly in central-west counties. Rural and eastern counties show significantly lower adoption, likely due to range anxiety, fewer charging stations, or less EV-friendly incentives.

-Additional analysis reveals that Jaguar leads the list with an average range of 193 miles. Notably, Tesla, despite its strong reputation, ranks in the middle due to the inclusion of multiple models with varying ranges in the dataset. Lesser-known brands such as Wheego Electric Cars and Think also perform well, likely due to outliers or smaller sample sizes influencing the results.


## 3. Can we predict electric range based on make, model year, and vehicle type? (Intro to ML)  

To explore this, we trained a machine learning model using features like vehicle make, model year, and electric vehicle type to predict electric driving range. We applied a log transformation to normalize the range values and used models such as Random Forest and Linear Regression to test performance. With an R² of 0.98 on the test set, the model demonstrates strong predictive capability.

[View the Jupyter Notebook with detailed steps here](3_Prediction_ML_2.ipynb) 


### Visualize the Data

```python
# Train-Test Split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Train Random Forest
model = RandomForestRegressor(random_state=42, n_estimators=100)
model.fit(X_train, y_train)
y_pred_log = model.predict(X_test)

# Reverse the log to get back to original scale
y_pred = np.expm1(y_pred_log)
y_true = np.expm1(y_test)

r2 = r2_score(y_true, y_pred)
print(f"R² on test set (back to original scale): {r2:.2f}")
```
### Results

![EV Distribution Across Washington Counties](/images/range_vs_year_by_make.png)
*Electric Vehicle Range Over Time by Manufacturer (2002–2025)*

### Insights:
-Make Matters: The linear model’s feature importance plot shows that the make of the vehicle is the most influential factor. Jaguar, Alfa Romeo, and Dodge are associated with higher predicted ranges, while older or niche brands like Think and Azure Dynamics pull the average down.

-Range Grows with Time: The scatter plot of range vs. model year shows a clear upward trend in electric ranges over time. Post-2018 models, especially from Tesla and Polestar, exhibit consistently higher ranges, reflecting improvements in battery tech and efficiency.

-PHEVs Lag Behind : Plug-in hybrid vehicles (PHEVs) show consistently lower predicted ranges than fully electric models. This distinction is critical for consumers evaluating EVs based on range alone and for policies encouraging full electrification.
