# Project: Automating the Download of HUD Homeless Population Reports

## Project Overview:
This Python project automates the process of downloading multiple HUD Homeless Populations and Subpopulations reports from 2005 to 2023 for Washington state. This automation was designed to simplify data acquisition for further analysis and validation.

## Technologies Used:
- **Python**: For scripting and automation.
- **`requests` library**: To make HTTP requests and download files from the web.
- **`os` library**: For handling file paths and directory creation.
- **Error Handling**: To manage any issues with file downloads or server availability.

---

## Python Code:

```python
import requests
import os

# List of years for which we want to download the PDFs
years = [2023, 2022, 2021, 2020, 2019, 2018, 2017, 2016, 2015, 2014,
         2013, 2012, 2011, 2010, 2009, 2008, 2007, 2006, 2005]

# Base URL structure for the reports
base_url = "https://files.hudexchange.info/reports/published/CoC_PopSub_State_WA_{}.pdf"

# Directory where the PDFs will be saved
download_dir = r"C:\Users\antho\OneDrive\Desktop\Jobs\Project Portfolio"

# Create the download directory if it doesn't exist
if not os.path.exists(download_dir):
    os.makedirs(download_dir)

# Loop through each year and download the corresponding PDF
for year in years:
    pdf_url = base_url.format(year)  # URL for each year's PDF
    pdf_name = f"CoC_PopSub_State_WA_{year}.pdf"  # Name of the PDF file
    pdf_path = os.path.join(download_dir, pdf_name)  # Path to save the file

    try:
        # Download the PDF
        response = requests.get(pdf_url)
        response.raise_for_status()  # Check if the request was successful

        # Save the PDF locally
        with open(pdf_path, "wb") as pdf_file:
            pdf_file.write(response.content)

        print(f"Downloaded: {pdf_name}")

    except requests.exceptions.HTTPError as http_err:
        print(f"Failed to download {pdf_name}: {http_err}")

print(f"Downloaded all available PDFs to {download_dir}.")
