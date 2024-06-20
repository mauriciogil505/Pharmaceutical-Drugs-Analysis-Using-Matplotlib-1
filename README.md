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

### Generate summary statistics.
### Create bar charts and pie charts.
### Calculate quartiles, find outliers, and create a box plot.
### Create a line plot and a scatter plot.
### Calculate correlation and regression.
### Finalize analysis.

