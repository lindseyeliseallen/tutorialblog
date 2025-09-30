# Importing & Visualizing: BMI vs Age
**Objective:** Learn how to create a scatter plot using Python, pandas, and matplotlib to explore patterns.

## Introduction
Understanding how to load in your own data to python and create visualizations of your data is import in finding trends. In this tutorial, we will be using the example of how BMI (Body Mass Index) changes with age in a small patient dataset. Visualizing these relationships helps identify trends, detect outliers, and generate hypotheses about health behaviors.

This guide is for those who want to practice data wrangling and visualization in Python. You’ll learn to:

 - Load and preview a dataset with pandas.

 - Plot scatter plots with matplotlib.

 - Add color coding and labels for better insights.

 - Use Markdown tables and optionally LaTeX for clarity.

### Step 1: Load the Dataset
Here is an example of how to load in your data using **pandas**. This is where we will put in our own data that we want to use for data visualization. 
Tips:
 - Make sure to import pandas before loading in the data.
 - Create a dictionary using keys (your column names: PatientID, Age, etc.)
 - Add your values (lists) to each key (these become the rows of your data).
 - Create a DataFrame object (named df below) that can be used for visualization.


### Sample patient dataset

```python
import pandas as pd
data = {
    'PatientID': [1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
    'Age': [25, 34, 28, 45, 52, 31, 37, 41, 29, 50],
    'BMI': [22.4, 27.1, 24.5, 29.3, 31.0, 26.2, 28.4, 30.1, 23.8, 32.0],
    'Gender': ['F', 'M', 'F', 'M', 'F', 'M', 'F', 'M', 'F', 'M'],
    'Department': ['Cardiology', 'Endocrinology', 'Neurology', 'Cardiology', 
                   'Endocrinology', 'Neurology', 'Cardiology', 'Endocrinology', 'Neurology', 'Cardiology']
}

df = pd.DataFrame(data)
```

### Step 2: Preview the Data
Before plotting, it is useful to view the data that you just imported to make sure there are no issues. Use the head() function to see a number of the first rows. Here is an example of how we would see the first 5 rows of our BMI vs. Age data:
```python
df.head(5)
```
| PatientID | Age | BMI  | Gender | Department    |
|-----------|-----|------|--------|---------------|
| 1         | 25  | 22.4 | F      | Cardiology    |
| 2         | 34  | 27.1 | M      | Endocrinology |
| 3         | 28  | 24.5 | F      | Neurology     |
| 4         | 45  | 29.3 | M      | Cardiology    |
| 5         | 52  | 31.0 | F      | Endocrinology |


### Step 3: Create a Scatter Plot
Now we will use our DataFrame to create a scatter plot. This is where we will use matplotlib to help make our plot. We will plot BMI vs. Age and use colors to distinguish genders.
Tips:
 - Make sure to import matplotlib in python.
 - Decide if there are any variables that you want to distinguish by color.
 - Enhance your graph by labling your plot and axes, adding gridlines, and a legend if you decide to color code.

```python
import matplotlib.pyplot as plt

# Color code by gender
colors = {'F': 'pink', 'M': 'blue'}

# Plot
plt.figure(figsize=(8,6))
for gender in df['Gender'].unique():
    subset = df[df['Gender'] == gender]
    plt.scatter(subset['Age'], subset['BMI'], label=gender, color=colors[gender], s=100)

# Add labels, legend, and gridlines
plt.xlabel('Age')
plt.ylabel('BMI')
plt.title('BMI vs Age by Gender')
plt.legend(title='Gender')
plt.grid(True)
plt.show()
```
