# Project Overview

This Python project performs the extraction, transformation, and loading (ETL) of PDF's to CSV's from 
https://www.hudexchange.info/programs/coc/coc-homeless-populations-and-subpopulations-reports/?filter_Year=&filter_Scope=State&filter_State=WA&filter_CoC=&program=CoC&group=PopSub 
HUD Homeless Populations and Subpopulations reports from 2005 to 2023. The script normalizes the data by cleaning the CSV files and ensuring that the data is formatted consistently. The cleaned data is then saved for further analysis.

## Technologies Used:

- **Python**: For scripting and automation.
- **Pandas library**: To handle data manipulation and cleaning.
- **os library**: For handling file paths and directory creation.
- **Error Handling**: To manage any issues with data inconsistencies.

## Python Code:

```python
import os
import pandas as pd

# Define directory paths
csv_directory = r'C:\Users\antho\OneDrive\Desktop\Jobs\Project Portfolio\CSV'
output_directory = r'C:\Users\antho\OneDrive\Desktop\Jobs\Project Portfolio\Cleaned'

# Ensure output directory exists
os.makedirs(output_directory, exist_ok=True)

# List all CSV files
csv_files = [f for f in os.listdir(csv_directory) if f.endswith('.csv')]

# Column headers for renaming (ensure these match your files)
expected_columns = ['household_type', 'emergency_shelter', 'transitional_housing', 'unsheltered', 'total_population']

# Function to clean and normalize the data
def clean_data(df):
    # Drop fully empty rows
    df_cleaned = df.dropna(how='all')

    # Ensure the correct number of columns
    if len(df_cleaned.columns) == 5:
        df_cleaned.columns = expected_columns
    else:
        print(f"Warning: Column mismatch. Skipping file with columns: {df_cleaned.columns}")
        return None

    return df_cleaned

# Process each CSV file
for file in csv_files:
    try:
        file_path = os.path.join(csv_directory, file)

        # Read CSV
        df = pd.read_csv(file_path)

        # Clean and normalize
        df_cleaned = clean_data(df)
        if df_cleaned is not None:
            # Save the cleaned data to a new CSV file
            output_file = os.path.join(output_directory, file.replace('tabula-', 'cleaned_'))
            df_cleaned.to_csv(output_file, index=False)
            print(f"Processed {file} successfully.")
        else:
            print(f"Error processing {file}: Column mismatch or missing data.")

    except Exception as e:
        print(f"Error processing {file}: {e}")

print("Data cleaning and normalization complete. Files are saved by year.")
How to Run:
Clone the repository using the following command:

bash
Copy code
git clone https://github.com/MrArod/WA_Homelessness.git
Install the required dependencies:

bash
Copy code
pip install pandas
Place your CSV files in the directory specified in the script (CSV directory).

Run the Python script to clean and normalize the data:

bash
Copy code
python etl_script.py
The cleaned CSV files will be saved in the Cleaned folder in your project directory.

