## Author
- **Kajola Gbenga**

- **Certified Data Scientist, Certified Data Analyst, Certified SQL Programmer**

- **www.linkedin.com/in/kajolagbenga**

# THE FIRST README EXPLANATION OF THE CODE

# Age Group Distribution Analysis

## Overview
This project analyzes the distribution of participants across different age groups using data from an Excel file. The analysis involves data cleaning, handling missing values, counting occurrences of each age group, and visualizing the results using a bar chart.

## Features
- Loads participant data from an Excel file.
- Cleans column names by removing hidden characters and whitespace.
- Handles missing values in the 'Age Group' column by filling them with 'Unknown'.
- Computes:
  - The count of participants in each age group.
  - The percentage breakdown of each age group.
- Generates a bar chart for visualization.

## Requirements
Ensure you have the following dependencies installed:

- `pandas`
- `matplotlib`
- `seaborn`

You can install them using:
```sh
pip install pandas matplotlib seaborn
```

## Usage
1. Ensure the Excel file (`UMERA BOOST 2.0 & 3.0.xlsx`) is available in the same directory as the script.
2. Run the script:
   ```sh
   python script.py
   ```
3. The output includes:
   - A table displaying the count of participants per age group.
   - A percentage breakdown of each age group.
   - A bar chart visualizing the distribution.

## Error Handling
- If the Excel file is missing or cannot be read, an error message will be displayed.
- If the 'Age Group' column is missing, the script will exit with a message.

## Visualization Details
- Uses the `viridis` color palette for clarity.
- The x-axis labels are rotated for better readability.
- Gridlines are added for enhanced visibility.
- A bar chart is created with `seaborn` for a clear representation of participant distribution.

## Line-by-Line Code Explanation

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```
- Import necessary libraries:
  - `pandas` for handling the dataset.
  - `matplotlib.pyplot` and `seaborn` for visualization.

```python
df = pd.read_excel("UMERA BOOST 2.0 & 3.0.xlsx", sheet_name="UMéRA 3.0")
```
- Reads the Excel file and loads the sheet `UMéRA 3.0` into a DataFrame.

```python
df.columns = df.columns.str.strip().str.replace(r'\u2060', '', regex=True)
```
- Cleans column names by removing leading/trailing whitespace and hidden characters.

```python
age_group_column = 'Age Group'
```
- Defines the column name storing age group information.

```python
df[age_group_column] = df[age_group_column].fillna("Unknown")
```
- Fills missing values in the 'Age Group' column with "Unknown".

```python
age_group_distribution = df[age_group_column].value_counts().sort_index()
```
- Counts occurrences of each unique age group and sorts them.

```python
plt.figure(figsize=(10, 6))
sns.barplot(x=age_group_distribution.index, y=age_group_distribution.values, palette='viridis', hue=age_group_distribution.index, legend=False)
```
- Creates a bar plot using `seaborn` to visualize age group distribution.

```python
plt.xlabel("Age Group")
plt.ylabel("Number of Participants")
plt.title("Distribution of Participants Across Age Groups")
plt.xticks(rotation=45)
plt.grid(axis='y', linestyle='--', alpha=0.7)
plt.show()
```
- Customizes plot labels, title, tick rotation, and grid style, then displays the chart.

```python
print("Age Group Distribution:\n")
print(age_group_distribution)
```
- Prints the numerical distribution of participants across age groups.

```python
age_group_percentage = (age_group_distribution / age_group_distribution.sum()) * 100
print("\nPercentage Breakdown of Age Groups:\n")
print(age_group_percentage.round(2).astype(str) + '%')
```
- Computes the percentage breakdown of each age group and prints the result.

## Output
```
Age Group Distribution:

Age Group
18 - 24    472
25 - 34    382
35 - 44    101
45+         25
Name: count, dtype: int64

Percentage Breakdown of Age Groups:

Age Group
18 - 24    48.16%
25 - 34    38.98%
35 - 44    10.31%
45+         2.55%
Name: count, dtype: object
```

## License
This project is licensed under the MIT License.





# THE SECOND README EXPLANATION OF THE CODE

# Age Group Distribution Analysis

## Overview
This project analyzes the distribution of participants across different age groups using data from an Excel file. The analysis includes data loading, cleaning, handling missing values, counting occurrences of each age group, and visualizing the results using a bar chart.

## Features
- Loads participant data from an Excel file.
- Cleans column names by removing hidden characters and whitespace.
- Checks if the 'Age Group' column exists in the dataset.
- Handles missing values by filling them with 'Unknown'.
- Computes:
  - The count of participants in each age group.
  - The percentage breakdown of each age group.
- Generates a bar chart with labeled values for visualization.

## Requirements
Ensure you have the following dependencies installed:

- `pandas`
- `matplotlib`
- `seaborn`

You can install them using:
```sh
pip install pandas matplotlib seaborn
```

## Usage
1. Ensure the Excel file (`UMERA BOOST 2.0 & 3.0.xlsx`) is available in the same directory as the script.
2. Run the script:
   ```sh
   python script.py
   ```
3. The output includes:
   - A table displaying the count of participants per age group.
   - A percentage breakdown of each age group.
   - A bar chart visualizing the distribution.

## Error Handling
- If the Excel file is missing or cannot be read, an error message is displayed, and the script exits.
- If the 'Age Group' column is missing, the script exits with an appropriate message.

## Line-by-Line Code Explanation

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```
- Import necessary libraries:
  - `pandas` for handling the dataset.
  - `matplotlib.pyplot` and `seaborn` for visualization.

```python
file_path = "UMERA BOOST 2.0 & 3.0.xlsx"
sheet_name = "UMéRA 3.0"
```
- Define the file path and sheet name from which data will be loaded.

```python
try:
    df = pd.read_excel(file_path, sheet_name=sheet_name)
    print("Data successfully loaded!")
except Exception as e:
    print(f"Error loading file: {e}")
    exit()
```
- Attempt to read the Excel file. If an error occurs (e.g., file not found), print an error message and exit.

```python
df.columns = df.columns.str.strip().str.replace(r'\u2060', '', regex=True)
```
- Clean column names by removing leading/trailing whitespace and hidden characters.

```python
age_group_column = 'Age Group'
```
- Define the column name storing age group information.

```python
if age_group_column not in df.columns:
    print(f"Column '{age_group_column}' not found in dataset.")
    exit()
```
- Check if the 'Age Group' column exists in the dataset. If not, print an error message and exit.

```python
df[age_group_column] = df[age_group_column].fillna("Unknown")
```
- Fill missing values in the 'Age Group' column with "Unknown".

```python
age_group_distribution = df[age_group_column].value_counts().sort_index()
```
- Count occurrences of each unique age group and sort them.

```python
print("\nAge Group Distribution:\n")
print(age_group_distribution)
```
- Print the numerical distribution of participants across age groups.

```python
age_group_percentage = (age_group_distribution / age_group_distribution.sum()) * 100
print("\nPercentage Breakdown of Age Groups:\n")
print(age_group_percentage.round(2).astype(str) + '%')
```
- Compute the percentage breakdown of each age group and print the result.

```python
plt.figure(figsize=(12, 7))
sns.barplot(x=age_group_distribution.index, y=age_group_distribution.values, palette='viridis', hue=age_group_distribution.index, legend=False)
```
- Create a bar plot using `seaborn` to visualize age group distribution.

```python
for index, value in enumerate(age_group_distribution.values):
    plt.text(index, value + 1, str(value), ha='center', fontsize=12, fontweight='bold')
```
- Add data labels above each bar in the bar chart for clarity.

```python
plt.xlabel("Age Group", fontsize=14)
plt.ylabel("Number of Participants", fontsize=14)
plt.title("Distribution of Participants Across Age Groups", fontsize=16, fontweight='bold')
plt.xticks(rotation=45, fontsize=12)
plt.yticks(fontsize=12)
plt.grid(axis='y', linestyle='--', alpha=0.7)
plt.show()
```
- Customize plot labels, title, tick rotation, and grid style, then display the chart.

- Computes the percentage breakdown of each age group and prints the result.

## Output
```
Age Group Distribution:

Age Group
18 - 24    472
25 - 34    382
35 - 44    101
45+         25
Name: count, dtype: int64

Percentage Breakdown of Age Groups:

Age Group
18 - 24    48.16%
25 - 34    38.98%
35 - 44    10.31%
45+         2.55%
Name: count, dtype: object

```

## License
This project is licensed under the MIT License.