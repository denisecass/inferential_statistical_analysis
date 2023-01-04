# Statistical_Performance_Analysis
**Python Libraries Used:**
- Matplotlib
- Matplotlib.pyplot
- Seaborn
- Pandas
- Numpy
- statsmodel.api

**Python Skills Used:**
- Create Line Plots and Box Plots 
- Understand Descriptive Statistics from the .describe() Functions
- Detect and Remove Outliers from the Dataset
- Subset and Filter DataFrames 
- Use For Loops to Loop Through Data
- Use Dual Axes to Plot Multiple Variables on Different Axes 
- Interpret Correlation Coefficients and Heatmaps
- Create and Assess the Quality of 'Fit' for Linear Regression Models 

# Part 1
**Tasks Completed:**

1. Imported each of the two data sources and stored them into their individual DataFrames. 
2. Printed descriptive statistics for each of the DataFrames using **.describe()** and **.info()**
3. Using the DataFrame, created a boxplot  and lineplot visualising this data.
4. Using the dataframe_raw dataset, created two boxplots specifically for when the pump had failed and when the pump wass working normally. 
5. Created two new variables called Q1 and Q3 using the dataframe_raw dataset. Q1 should contain the 25th percentile for all columns in the DataFrame. Q3 should contain the 75th percentile  for all the columns in the DataFrame.
6. After defining Q1 and Q3, calculated the interquartile range **(IQR = Q3 - Q1)** for all columns in the DataFrame and printed it to the screen.
7. Defined two new variables, Lower_Limit and Upper_Limit, calculated as:
     -  Lower_Limit = Q1 - 1.5 * IQR </li>
     -  Upper_Limit = Q3 + 1.5 * IQR </li> 
8. Used Lower_Limit and Upper_Limit with an OR (|) condition to filter the DataFrame to include *only* the outliers.
9. Found the percentage of data that remainsed after removing the outliers from the dataframe_raw dataset.
10. Made a new DataFrame called no_outliers and using the ~ operator, remove all the outliers from the DataFrame.
11. Created two box plots using the no_outliers dataframe as per below:
     - A boxplot when PUMP FAILURE is 1 (Failure)
     - A boxplot when PUMP FAILURE is 0 (Normal Behaviour)
12. Used the syntax below to loop through the dataframe_raw dataset, plotting every variable individually, against the Pump Failure to better identify trends.
      - for item in ListOfVariables:
        first_axis = dataframe[___].plot #Looping through every item in the dataframe.
        second_axis = first_axis.twinx() #The Twinx function is used to ensure we share the X-Axis for both plots
        second_axis.plot(dataframe['ColumnOfInterest'], color='teal')
        plt.title(item)
        plt.show()
13. Set the **index of the dataframe_stdev** dataset to the TIMEFRAME (DD/MM/YYYY) attribute.
14. Used the List_Of_Variables created in Step 12 to replot all of the numerical variables in the dataframe_stdev for the following time periods:
     10/12/2014 12:00 to 10/12/2014 14:30.
15. Created a heatmap with Seaborn's heatmap function that clearly shows the correlations (R) for all variables using the dataframe_raw dataset.
16. Used the correlated DataFrame made earlier to create a barplot that shows the correlated features against PUMP FAILURE (1 or 0), in descending order.
17. Utilized Seaborn's heatmap function to create a heatmap that clearly shows the correlations (including R) for all variables using the dataframe_stdev dataset.
18. Used the OLS Regression Model in the statsmodel.api library to create a regression equation that models the Pump Failure (Y-Variable) against all of the independent variables in the dataframe_raw dataset and the dataframe_stdev dataset.
19. Extracted the Coefficients from the regression_model using the .params method, and created a bar plot that identifies which coefficients react most strongly with respect to Pump Failure.
20. Create a new column in the dataframe_stdev, called, 'Prediction'. 
21. Used the regression equation to create and apply the .predict() function to the independent variables in the dataframe_stdev dataset, resulting in a column full of the regressive predictions.
22. Created a Dual-Axis Plot with the following axes items:
     - Axes One contains: Volumetric Flow Meter 2, Pump Efficiency and Horse Power 
     - Axes Two contains: Pump Failure (1 or 0) and Prediction

**Questions Answered:**
1. When looking at the Descriptive Statistics for both datasets; pay attention specifically to the standard deviation and mean. 
What do you observe when you compare the dataframe_raw standard deviation and mean, versus the dataframe_stdev standard deviation and mean?
    - When looking at the standard deviation (std) and the mean values for both the dataframe_raw data and dataframe_stdev data, it appears as though the std and mean vary greatly from each other, which implies that the data is not reliable.
2. What can be observed from the boxplot and line plots for both the dataframe_raw and dataframe_stdev datasets?
     - Although the raw data looks fairly stable with its values and quartile ditribution, the stdev data shows a higher number of outliers (especially with pump torque), which could lead to misinterpretation of the dataset. 
3. What can be noticed when comparing the dataset in this manner?
     - There are a lot of outliers in all of the boxplots, particularly in the Stdev Pump Normal. Scattered data points like this can lead to erroneous conclusions.
4. Are there any particular trends when looking at the data in this way? Has it made it easier to see which variables *might* be reacting more strongly to the Pump Failure than others?
     - All of the variables are being affected by Pump Failure, especially Pump Speed, Pump Torque, Ambient Temperature, and Horsepower (as made evident by the spikes in measured values during Pump Failure). There is also small spike, followed by a sudden drop in Volumentric Flow Meters 1 and 2, and Pump Efficiency.

# Part 2

**Tasks Completed:**

1. Used Seaborn's heatmap function, to create a heatmap that clearly shows the correlations (R) for all variables using the dataframe_raw dataset.
2. Made a barplot that shows the correlated features against PUMP FAILURE (1 or 0), in descending order, using the correlated DataFrame created earlier.
3. Formulated a heatmap (using Seaborn) that clearly shows the correlations (including R) for all variables using the dataframe_stdev dataset.
4. Created a OLS Regression Model in the statsmodel.api library, making a regression equation that models the Pump Failure (Y-Variable) against all the independent variables in the dataframe_raw and dataframe_stdev datasets by: 
   - Establishing two DataFrames named, independent_variables and dependent_variables. In this case, the Dependent Variable is Pump Failure (1 or 0).
   - Adding a constant to the Independent Dataframe via the following syntax:
    independent_variables = sm.add_constant(independent_variables)
   - Storing and fitting the model with the below syntax:
    regression_model = sm.OLS(dependent_variable,independent_variable).fit() 
   - Printing the regression_model.summary() to view the Regression Statistics 
5. Used the .params method, extract the Coefficients from the regression_model, and formulated a bar plot that identifies which coefficients react most strongly with respect to Pump Failure. 
6. Added a new column in the dataframe_stdev, called, 'Prediction'. 
7. Applied the .predict() function to the independent variables in the dataframe_stdev dataset (using the regression equation created in the previous step) to get a column full of the regressive predictions.
8. Created a Dual-Axis Plot with the following axes items:
    - Axes One: Volumetric Flow Meter 2, Pump Efficiency and Horse Power 
    - Axes Two: Pump Failure (1 or 0) and Prediction

**Questions Answered:**
1. Which variables seem to correlate with Pump Failure?
    - Volumetric Flow Meters 1 & 2 and Pump Efficiency show the highest correlation with Pump Failure. 
2. Do any variables stand out? 
    - All of the variables ('Volumetric Flow Meter 1', 'Volumetric Flow Meter 2', 'Pump Speed (RPM)','Pump Torque ', 'Ambient Temperature', and 'Pump Efficiency') appear to be correlated to PUMP FAILURE by around 0.6, except for 'Horse Power' at 0.69. 
3. Compare the Models you've created and observe the R Squared displayed for each model. Which model seems better and why? 
    - The R^2 value is 0.3 appears to show a weak correlation in the raw dataset. This indicates that this is not an effective model for predicting or explaining Pump Failure. However, the rolling stdev dataset shows an R^2 value of 0.7, which is much closer to 1, thus showing a stronger correlation to Pump Failure. This should be a fairly reliable model to predict/explain pump failure events.
