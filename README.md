# Traffic Accident Data Analysis
## Overview
This project involves analyzing traffic accident data to uncover patterns and trends based on various factors such as vehicle type, weather conditions, and road surface conditions. The analysis is conducted using Python libraries including Pandas, NumPy, Matplotlib, and Seaborn.

## Dataset
The dataset used in this project is a CSV file named Task5.csv. It includes the following columns:

`Time:` Time of the accident.
`Type_of_vehicle:` Type of vehicle involved in the accident.
`Area_accident_occured:` Area where the accident occurred.
`Weather_conditions:` Weather conditions at the time of the accident.
`Road_surface_conditions:` Road surface conditions at the time of the accident.
## Dependencies
To run this project, you need to have the following Python libraries installed:

`pandas`
`numpy`
`matplotlib`
`seaborn`
You can install these dependencies using pip:

```bash
pip install pandas numpy matplotlib seaborn
```
## Getting Started
### Clone the Repository:

```bash
git clone https://github.com/yourusername/traffic-accident-analysis.git
cd traffic-accident-analysis
```
### Download the Dataset:

Ensure that the dataset file Task5.csv is placed in the project directory.

### Run the Analysis Script:

Execute the Python script to perform data analysis and generate visualizations:

```bash

python analysis.py
```
Make sure to replace analysis.py with the actual name of your script if it differs.

## Code Overview
**Data Import and Inspection:**
    
    Loads the dataset and inspects its structure and summary statistics.
    
**Data Cleaning:**

Converts the Time column to a datetime format and extracts the hour from it.

**Aggregation:**

Computes the number of accidents by hour, weather conditions, and road surface conditions.

**Visualization:**

#### Scatter Plot: 
Displays the distribution of accidents based on vehicle type and accident area (consider replacing with count plots if Type_of_vehicle and Area_accident_occured are categorical).

#### Bar Plots:
Show the number of accidents by weather conditions and road surface conditions.

## Visualizations:
#### Accidents by Type of Vehicle: 
A count plot illustrating the number of accidents involving different types of vehicles.

#### Accidents by Area of Occurrence: 
A count plot showing the number of accidents in various areas.

#### Accidents by Weather Condition: 
A bar plot representing the number of accidents under different weather conditions.

#### Accidents by Road Condition:
A bar plot depicting the number of accidents based on road surface conditions.

## Script Details
**Import Libraries:**
```bash
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```
**Load Data:**

```bash
data = pd.read_csv('/home/rguktong/Desktop/Task5.csv')
```
**Data Overview:**

```bash
print(data)
print(data.info())
print(data.head())
print(data.describe())
print(data.columns)
```
**Data Cleaning:**
```bash
print(data.isnull().sum())
data['Time'] = pd.to_datetime(data['Time'], format='%H:%M:%S', errors='coerce')
data['hour'] = data['Time'].dt.hour
```
**Accident Aggregation:**

```bash
accidents_by_hour = data.groupby('hour').size()
accidents_by_weather = data['Weather_conditions'].value_counts()
accidents_by_road_condition = data['Road_surface_conditions'].value_counts()
```
**Visualizations:**

### Accident Hotspots Scatter Plot:

```bash
plt.figure(figsize=(20, 6))
sns.scatterplot(x='Type_of_vehicle', y='Area_accident_occured', data=data, alpha=0.5)
plt.title('Accident Hotspots')
plt.show()
```

### Accidents by Weather Condition Bar Plot:

```bash
plt.figure(figsize=(12, 6))
sns.barplot(x=accidents_by_weather.index, y=accidents_by_weather.values)
plt.title('Accidents by Weather Condition')
plt.xticks(rotation=45)
plt.show()
```
### Accidents by Road Condition Bar Plot:

```bash
plt.figure(figsize=(12, 6))
sns.barplot(x=accidents_by_road_condition.index, y=accidents_by_road_condition.values)
plt.title('Accidents by Road Condition')
plt.xticks(rotation=45)
plt.show()
```
## Data File
Ensure that the CSV file Task5.csv is present at the specified path /home/rguktong/Desktop/Task5.csv. The dataset should contain columns such as Time, Weather_conditions, Road_surface_conditions, Type_of_vehicle, and Area_accident_occured.

## Notes
Adjust the path to the CSV file based on your local setup.
Modify the script if the dataset schema differs or if additional cleaning and preprocessing are needed.
## License
This script is provided as-is. You are free to use, modify, and distribute it under your own terms.

