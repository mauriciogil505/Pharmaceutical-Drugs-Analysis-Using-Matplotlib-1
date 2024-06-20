# Pharmaceutical-Drugs-Analysis-Using-Matplotlib-1

### Summary
A data analysis and visualization project using Matplotlib to evaluate the efficacy of various drug regimens for treating squamous cell carcinoma in mice, based on data from Pymaceuticals, Inc.
### Prepare the data.
Read the CSV Files:

pd.read_csv(mouse_metadata_path): Reads the mouse dataset CSV file into a Pandas DataFrame.
pd.read_csv(study_results_path): Reads the study results dataset CSV file into a Pandas DataFrame.

Merge the DataFrames:

pd.merge(mouse_metadata, study_results, on='Mouse ID'): Merges the "mouse dataset" and "study results" DataFrames based on the 'Mouse ID' column. This creates a combined DataFrame where each row contains information from both datasets for each mouse.

Count Unique Mice:

data_combined['Mouse ID'].nunique(): Calculates the number of unique 'Mouse ID' values in the combined DataFrame. This gives the total count of unique mice in the dataset.

Print the Result:

print(f'The number of unique mice in the dataset is: {unique_mice}'): Prints the total number of unique mice identified in the dataset using f-string formatting.

### Generating Summary Statistics.

Summary of my Data Handling and Cleaning Process
Identifying and Handling Duplicates:
Identify the Duplicates:

The code checks for duplicate rows in the combined dataset using the 'Mouse ID' and 'Timepoint' columns.
Filter Duplicates:

It filters the dataset to isolate rows that are identified as duplicates based on 'Mouse ID' and 'Timepoint'.
Print Duplicates:

The filtered dataset containing duplicate entries is printed to make review and analysis easier to read.
Removing Duplicate Mouse ID:
Identify the Duplicate Mouse ID:

Once duplicates are identified, the unique 'Mouse ID' associated with duplicates is extracted for further action.
Filter the Data:

Rows corresponding to the identified duplicate 'Mouse ID' are removed from the dataset to isolate the unique mouse IDs.
Print the Cleaned DataFrame:

The resulting cleaned dataset is printed to confirm that the duplicate mouse data has been effectively removed.
Counting Unique Mouse IDs:
Count Unique Mouse IDs:

The cleaned dataset is analyzed to count the number of unique 'Mouse ID' entries using the nunique() function.
Print the Number of Mice:

The total count of unique mice remaining in the cleaned dataset is printed for validation and accuracy.

Use case: By doing this, you ensure that the dataset is free from duplicate entries, which will skew analytics and interpretations of the data.

Summary of Drug Regimen Analysis
Using Grouping and Calculating Statistics:
Grouping Data by Drug Regimen:

The cleaned dataset is organized into groups based on different drug regimens for analysis.

Calculate Mean Tumor Volume:
The objective for each drug regimen, is to average the tumor volume to understand the typical tumor size under each treatment.

Calculate Median Tumor Volume:
The median tumor volume is calculated for each drug regimen which represents the middle of the distribution.

Calculate Variance of Tumor Volume:
Variance, which indicates the spread of tumor volumes around the mean.

Calculate Standard Deviation:
Standard deviation, a measure of the amount of variation or dispersion of tumor volumes from the mean, is computed.

Calculate the Standard Error of the Mean (SEM):
This measures the precision of the sample mean estimate; calculated for each drug regimen.

A new DataFrame is created to consolidate all of these calculated statistics (mean, median, variance, standard deviation, and SEM) for each of the 4 drug regimen.

Displaying Results:
Display the Summary DataFrame:

The summary DataFrame is presented, providing an overview of the tumor volume statistics for each of the 4 drug regimens.

Use cases:
Insightful data: By analyzing tumor volume statistics across drug regimens, this reveals insights into treatment effectiveness.

Treatment Comparison: Enables comparison of treatment outcomes based on tumor size metrics, aiding in treatment selection and refinement.

Data-driven Decisions: Facilitates informed decisions by presenting clear and structured data summaries, supporting further research and decision-making processes.

This structured analysis enhances understanding of drug efficacy in tumor treatment 

### Creating Bar Charts and Pie Charts.
Bar Charts:
Using Pandas plot() Method-
timepoints_count = cleaned_data['Drug Regimen'].value_counts(): Computes the number of timepoints for each drug regimen.
.plot(kind='bar', figsize=(8, 6), color='skyblue', alpha=0.7): Creates a bar plot using Pandas, specifying figure size, color, and transparency.
Various plt functions set the plot title, labels, rotation of x-axis labels, and layout.
Using PyPlot Method-
drug_regimens = timepoints_count.index: Retrieves the drug regimen names from timepoints_count index.
plt.bar(drug_regimens, timepoints_count, color='lightcoral', alpha=0.7): Creates a bar plot using Matplotlib's bar() function.
Other plt functions set the plot title, labels, rotation of x-axis labels, and layout.

Pie Charts:

Using Pandas plot() Method for Gender Distribution-
gender_counts = cleaned_data['Sex'].value_counts(): Computes the count of female and male mice.
.plot(kind='pie', autopct='%1.1f%%', colors=['blue', 'pink'], startangle=140): Generates a pie chart with percentages using Pandas.
Various plt functions set the plot title, y-label (removed here), equal axis aspect ratio, and layout.

Using Matplotlib's pyplot Methods for Gender Distribution
labels = gender_counts.index and sizes = gender_counts.values: Extracts labels (gender categories) and sizes (counts) from gender_counts.
plt.pie(sizes, labels=labels, autopct='%1.1f%%', colors=['blue', 'pink'], startangle=140): Creates a pie chart using Matplotlib's pie() function.
Other plt functions set the plot title, equal axis aspect ratio, and layout.

### Calculation of quartiles, finding outliers, and creating a Box Plot.

Identifying the Promising Treatments

First, we focus on specific treatments (Capomulin, Ramicane, Infubinol, and Ceftamin) to assess their effectiveness in reducing tumor sizes.

Finding the Final Tumor Volume

For each mouse, we determine the last recorded timepoint, which gives us the final measurement of the tumor volume.

Aggregating the Data

We compile this data into a grouped DataFrame, merging it with the original dataset to obtain tumor volumes at the last timepoint.

Determining Outliers

Using statistical methods, we calculate the Interquartile Range (IQR) for each treatment group. Outliers, which fall outside 1.5 times the IQR above the third quartile or below the first quartile, are identified.

Creating a Box Plot for Visualization
Visualizing Data Distribution

To provide a clear overview, we use box plots. These graphs illustrate the distribution of final tumor volumes across different treatments, highlighting any outliers.

Interpreting the Box Plot

Box: Represents the interquartile range (IQR) which encompasses the middle 50% of the data.
Whiskers: Extend to the furthest data points within 1.5 times the IQR.
Points Beyond Whiskers: Indicate potential outliers.

### Creating a Line Plot and Scatter Plot.

Selecting a Mouse

We choose a specific mouse that was treated with Capomulin (for this I chose the first Mouse ID that was treated with Capomulin 's185').

Filtering Data

We filter the dataset (cleaned_data) to extract time points and corresponding tumor volumes for the chosen mouse.

Plotting the Data

Using Matplotlib, we create a line plot where:

X-axis represents time points (in days).
Y-axis represents tumor volume (in cubic millimeters).
Visualizing the Trend

This plot helps visualize how the tumor volume changes over time for the selected mouse, providing insights into the effectiveness of Capomulin treatment.

Creating a Scatter Plot: Mouse Weight vs. Average Tumor Volume for Capomulin Regimen
Grouping Data

We group the cleaned_data by 'Mouse ID' and calculate the average tumor volume and weight for mice treated with Capomulin.

Plotting the Data

Using Matplotlib, we create a scatter plot where:

X-axis represents mouse weight.
Y-axis represents average tumor volume.
Analyzing the Correlation

This plot helps us visualize if there’s any correlation between mouse weight and tumor volume, offering insights into potential relationships between these variables.

### Calculation of correlation and regression.

Grouping and Calculating Mean

First, we group the cleaned_data by 'Mouse ID' and calculate the mean tumor volume (avg_tumor_volumes) and weight (weights) for mice treated with the Capomulin regimen.

Calculating Correlation Coefficient

Using the pearsonr function from scipy.stats, we calculate the Pearson correlation coefficient (r_value) between mouse weight and average tumor volume. This coefficient ranges from -1 to 1 and indicates the strength and direction of the linear relationship between the two variables.

Fitting Linear Regression Model

We use linregress from scipy.stats to fit a linear regression model to the data. This model estimates the linear relationship between mouse weight (independent variable) and average tumor volume (dependent variable). The slope (slope) and intercept (intercept) of the regression line are computed.

Plotting Regression Line

Using Matplotlib, we plot the scatter plot of mouse weight against average tumor volume. Additionally, we overlay the fitted regression line to visualize the trend and relationship between the variables.

### Final analysis.
The analysis provided insights into drug treatment effectiveness to fight tumors (especially Capomulin). Variables explored were the distribution of mice by sex, and correlations between mouse characteristics and tumor sizes. These findings would help treatment plans and clinical research trials.

### Credit: Class notes, peer groups, class recordings, XPert Learning Assistant, Stack overflow, Youtube videos

