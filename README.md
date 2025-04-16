# Electric Vehicle Adoption Analysis in Washington State Model Year (2002–2025)

# Overview

This project explores the evolution and strategic implications of electric vehicle (EV) adoption in Washington State from 2002 to 2025. Motivated by the growing shift toward electric mobility and sustainability, the analysis investigates key trends in EV types, geographic distribution, and vehicle performance. Using real-world registration data, the goal is to provide insights that can guide automakers, policymakers, and infrastructure planners.

The data sourced from [Kaggle](https://www.kaggle.com/datasets/ricardobj/electric-vehicle-population) which provides a foundation for my analysis. By combining exploratory analysis with a bit of machine learning models, this project offers a comprehensive view of where EV adoption is headed and how the industry can adapt.

# The Questions
These were the central questions explored in the project:
1. How has electric vehicle (EV) adoption evolved in Washington State by model year, make, and vehicle type?
2. What is the geographic distribution of EVs across Washington counties, and how does electric range vary by make?
3. Can we predict electric range based on make, model year, and vehicle type? (Intro to ML)

# Tools I Used

To carry out this analysis, I used the following tools and technologies:

**Python:** Main programming language for data analysis and modeling. I also used the following Python libraries:
- **Pandas:** Data wrangling and manipulation
- **Matplotlib & Seaborn:** Data visualization
- **Scikit-learn:** Building and evaluating predictive models
- **Geopandas:** Mapping EV distribution across counties

**Jupyter Notebooks:** Interactive environment for coding and documenting analysis

**Visual Studio Code:** My go-to for executing my Python scripts.

**Git & GitHub:** Essential for version control and sharing my Python code and analysis, ensuring collaboration and project tracking.

# What I Learned

This project deepened my understanding of electric vehicle adoption patterns and gave me hands-on experience with geospatial data, time-series analysis, and introductory machine learning. Some specific takeaways include:

- **EV Market Dynamics:** I gained insights into how consumer preferences are shifting toward Battery Electric Vehicles (BEVs), especially post-2015, and how certain makes dominate market share.

- **Geospatial Analysis:** Working with geographic data using GeoPandas helped me visualize EV distribution across counties and recognize the importance of location in adoption trends.

- **Predictive Modeling:** I learned how to use regression models to predict EV range, and how categorical encoding, log transformation, and feature importance affect model performance.


# Insights

This project uncovered several key insights into electric vehicle trends and market dynamics in Washington State:

**BEVs Lead the Market**  
Battery Electric Vehicles (BEVs) have surged in popularity since 2015, with a sharp rise from 2021–2023, far outpacing Plug-in Hybrids (PHEVs). This reflects growing trust in fully electric models and improved range options.

**EV Adoption Is Regionally Concentrated**  
King County alone has nearly 120,000 EVs—over three times more than any other county—driven by urban infrastructure, higher income levels, and strong policy incentives. The Puget Sound region emerges as the state's EV hub.

**Make Predicts Range**  
Vehicle make is the strongest indicator of electric range. Premium brands like Jaguar and Alfa Romeo offer longer ranges, while PHEVs and lesser-known makes trail behind—highlighting differences in technology investment.


# Challenges I Faced

Every project brings its own hurdles, and this one offered a great opportunity for learning through problem-solving:

- **Messy Data:** The dataset had inconsistencies, particularly in vehicle make names and missing range values, requiring thoughtful cleaning and preprocessing.

- **Geospatial Integration:** Merging EV data with shapefiles for Washington counties was a new and complex task, involving careful handling of coordinate systems and joins.

- **Model Interpretation:** Making sense of residual plots and model performance required experimenting with multiple regression techniques and transformations to ensure interpretability.

# Conclusion

This project provided a comprehensive view of the electric vehicle landscape in Washington State and highlighted the fast-growing preference for fully electric vehicles. With strong regional patterns and evolving vehicle technology, this analysis reinforces the importance of aligning strategy with real-world adoption trends.

Going forward, this foundation can be expanded with real-time data updates, policy overlays, and consumer behavior metrics. The insights gained not only support data-driven decisions for automakers and planners but also demonstrate the power of combining analytics with domain knowledge in transportation and sustainability.


[> Start reviewing the questions and insights](/Python/README.md)

[> Take a closer look at the data](/Python/)