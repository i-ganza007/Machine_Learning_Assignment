**Fuel Economy Dataset Analysis
**
This project analyzes a dataset on fuel economy and emissions using Python. The primary objective is to explore the relationship between vehicle engine displacement and CO2 emissions using data visualization techniques.

<hr/>

**Project Overview
**
The project includes the following tasks:

Load the Dataset: Import and read the fuel_econ-1.csv dataset.

Define Bins for Visualization: Create bins to categorize engine displacement and CO2 emission data.

Generate a 2D Histogram: Visualize the relationship between engine displacement and CO2 emissions.

Generate Additional Visualizations: Analyze CO2 emissions distribution and variable correlations.

Annotate and Interpret Results: Use the graphs to understand the data relationships.

<hr/>

**Code Walkthrough
**
**Import Libraries
**
import numpy as np 
import pandas as pd
import seaborn as sb 
import matplotlib.pyplot as plt

These libraries are essential for numerical analysis, data manipulation, and visualization.

**Load the Dataset
**
fuel_econ = pd.read_csv('./fuel_econ-1.csv')

The dataset is stored in a Pandas DataFrame named fuel_econ.

**Define Bins
**
bins_x = np.arange(0.6, fuel_econ['displ'].max() + 0.4, 0.4)
bins_y = np.arange(0, fuel_econ['co2'].max() + 50, 50)

Custom bins for engine displacement (in liters) and CO2 emissions (in grams per mile) are created to improve visualization.

**Generate a 2D Histogram
**
plt.hist2d(
    data = fuel_econ, x = 'displ', y = 'co2', 
    bins = [bins_x, bins_y], cmap = 'viridis_r', cmin = 0.5
)
plt.colorbar()
plt.xlabel('Displacement (l)')
plt.ylabel('CO2 (g/mi)')

This generates a heatmap-like 2D histogram illustrating the relationship between engine displacement and CO2 emissions.

**Generate a Histogram of CO2 Emissions
**
plt.figure(figsize=(10, 6))
plt.hist(fuel_econ['co2'], bins=20, color='green', edgecolor='black')
plt.title('Histogram of CO2 Emissions')
plt.grid(True)
plt.show()

This histogram represents the distribution of CO2 emissions in the dataset.
Generate a Correlation Heatmap

numeric_columns = fuel_econ.select_dtypes(include=['float64', 'int64'])

# Calculating the correlation matrix
corr_matrix = numeric_columns.corr()

# Plotting the heatmap
plt.figure(figsize=(12, 10))
sb.heatmap(corr_matrix, annot=True, cmap='coolwarm', fmt=".2f", linewidths=0.5)
plt.title('Correlation Heatmap of Fuel Economy Data')
plt.show()

This heatmap visualizes the correlations between numerical columns in the dataset, helping identify relationships between variables.

<hr/>

**Visual Outputs
**
**Graph 1: Displacement vs. CO2 Emissions
**
The heatmap represents engine displacement on the x-axis and CO2 emissions on the y-axis. Data density is depicted using color intensity:

X-Axis: Engine Displacement (liters)

Y-Axis: CO2 Emissions (g/mi)

Color Bar: Indicates the density of data points for each category



**Graph 2: Histogram of CO2 Emissions
**
The histogram shows the distribution of CO2 emissions across all vehicles:

X-Axis: CO2 Emissions (g/mi)

Y-Axis: Frequency (number of vehicles)



Graph 3: Correlation Heatmap

This heatmap represents the correlations between numerical variables in the dataset. Key insights:

Dark red indicates strong positive correlation.

Dark blue indicates strong negative correlation.

<hr/>
**Key Observations
**
Vehicles with higher engine displacement generally emit more CO2.

CO2 emissions exhibit a skewed distribution with a concentration around specific values.

Strong correlations exist between some variables, as visualized in the heatmap.

<hr/>
**Future Improvements
**
Perform regression analysis to better understand relationships between variables.

Extend the analysis to include additional categorical variables, such as fuel type or transmission type.

Develop a machine learning model to predict CO2 emissions based on vehicle characteristics.

<hr/>
**Contributing
**
Contributions to improve the analysis and extend its scope are welcome. Please fork the repository and submit a pull request.
<hr/>

License

This project is licensed under the MIT License.
