SEC D-Type Filings Data Analysis, Visualization & CRM Data Preparation

This project provides a comprehensive suite of Python scripts for processing, analyzing, visualizing, and preparing SEC D-type filings data for import into a Customer Relationship Management (CRM) system. The code covers several key functionalities:

Interactive Dashboard:
A Dash/Plotly-based interactive dashboard (designed for Jupyter Notebook) that reads SEC filings CSV files from a ZIP archive, allows filtering by year, quarter, state, and funding amount, displays the filtered data in a table, and provides an option to export the results to CSV.
State-Level Analysis & Visualizations:
Multiple scripts generate state-specific metrics and visualizations including:
Calculating percentage growth in filings over time.
Creating choropleth maps to display filing percentages and total income raised by U.S. state.
Plotting time series for filing growth based on user-selected state input.
Versatile Data Filtering & Column Customization:
Interactive command-line functions allow users to apply multiple filters (e.g., state, fully subscribed offerings, funding amount, equity offerings, industry) and interactively customize columns to display, making the dataset ready for CRM integration.
CRM Data Preparation:
The project focuses on transforming and cleaning the filings data so that it can be readily imported into a CRM system. This involves:
Combining and enriching multiple CSV files with additional metadata (Year, Quarter).
Renaming and selecting relevant columns.
Converting financial fields to numeric types and handling non-numeric entries.
Cleaning redundant or unwanted strings.
Producing a final, clean CSV file (cleaned_data.csv) that can be imported into a CRM system for further customer relationship management and analysis.
SEC EDGAR Downloader & XML Parser:
A script that uses the SEC’s EDGAR index files and API to:
Download daily or quarterly index files.
Filter for Form D filings.
Retrieve and parse the associated XML filings to extract detailed issuer, related persons, and offering information.
Clean and export the final data to CSV.
Table of Contents

Overview
Prerequisites
Data Requirements
Installation
Usage
1. Interactive Dashboard
2. State-Level Analysis & Visualizations
3. Versatile Data Filtering & Column Customization
4. CRM Data Preparation
5. SEC EDGAR Downloader & XML Parser
Code Structure Overview
Additional Notes
License
Contact
Overview

This project is designed to help users work with SEC D-type filings data by:

Extracting and Combining Data:
Reading CSV files from a ZIP archive (covering data from 2014 to 2024) and appending additional metadata.
Interactive Analysis & Visualization:
Providing an interactive dashboard and state-level visualizations that help users explore and analyze filing trends.
Versatile Filtering and Customization:
Allowing users to interactively filter the data and customize the columns to produce a dataset that meets specific analysis or CRM import requirements.
CRM Data Preparation:
Transforming and cleaning data for import into a CRM system by creating a final, clean CSV file. This file is formatted to meet typical CRM import requirements, ensuring that key fields such as issuer details, offering amounts, and state information are correctly formatted and organized.
SEC EDGAR Integration:
Downloading and parsing SEC EDGAR filings to further enrich the dataset with detailed XML-based information.
Prerequisites

Python Version: Python 3.7 or later.
Development Environment:
– Jupyter Notebook or JupyterLab (for the interactive dashboard)
– Command-line or IDE for running other scripts
Python Packages:
pandas
plotly
dash and jupyter_dash
dash_bootstrap_components
dash_table
requests
sec_edgar_downloader (if using SEC EDGAR download functionality)
xml (included in Python’s standard library)
Install these dependencies via pip:

pip install pandas plotly dash jupyter-dash dash-bootstrap-components requests sec-edgar-downloader
Data Requirements

Data Source: A ZIP file named Data.zip located in the project directory.
File Format: The ZIP file should contain CSV files named by year and quarter (e.g., 2014_QTR1.csv, 2022_QTR3.csv).
Extraction Directory: The scripts extract the files into a folder named extracted_data.
Installation

Clone or download the repository.
Ensure that Data.zip is present in the project root.
Install the required dependencies as described above.
Usage

1. Interactive Dashboard for SEC D-Type Filings
Description:
The dashboard reads and combines CSV files from the ZIP archive, then provides interactive filtering by:
Year
Quarter
State
Total Amount Offered (using a range slider)
It displays the filtered results in a table and allows exporting the filtered dataset to CSV.
How to Run:
Open the code in a Jupyter Notebook.
Run the cell containing the dashboard code.
Use the dropdown menus and slider to filter the data.
View the resulting data table and click the "Export to CSV" button to download the results.
2. State-Level Analysis & Visualizations
This section includes several scripts:

Growth Analysis:
Processes filings data across years and quarters to calculate the percentage growth in filings by state.
Usage: Run the script, and when prompted, input a state abbreviation (e.g., CA, TX). A Plotly line chart will display the yearly growth for that state.
Jurisdiction Percentage Choropleth:
Extracts a specific quarterly CSV (e.g., 2022_QTR4.csv), calculates the percentage of filings by jurisdiction vs. physical state, and displays the result as a choropleth map of the USA.
Total Income Choropleth:
Aggregates total income raised by state from a specified CSV (e.g., 2022_QTR3.csv) and visualizes it with a choropleth map.
How to Run:
Execute the respective script in your Python environment (or separate Jupyter Notebook cells) and follow any on-screen prompts for input.
3. Versatile Data Filtering & Column Customization
Versatile Filtering:
The versatile_filter(df) function allows interactive, command-line filtering of the filings DataFrame.
Filters include:
State or Country (physical location)
Fully subscribed offerings
Funding amount range
Equity offerings
Industry
Column Customization:
The modify_columns(df) function lets users add or remove columns interactively to customize the data view.
How to Run:
Run the script (or the cell in a Jupyter Notebook) and follow the interactive prompts to apply/update filters and adjust the columns displayed.
4. CRM Data Preparation
Description:
In addition to analysis and visualization, this project prepares data for import into a CRM system. The data preparation process includes:
Data Cleaning: Handling missing values, converting financial fields to numeric types, and removing redundant strings.
Column Customization: Allowing users to select only the columns relevant for CRM import.
Final Export: The cleaned and customized data is saved as cleaned_data.csv, which can be imported into your CRM system.
How to Run:
Run the full data processing pipeline (including interactive filtering and column customization).
Once the data is transformed, review the output displayed by the modify_columns(df) function.
The final output is written to cleaned_data.csv—ready for CRM import.
5. SEC EDGAR Downloader & XML Parser
Description:
This script interacts with the SEC EDGAR system to download daily or quarterly index files, filter for Form D filings, download the XML files for those filings, and parse the XML to extract detailed information (issuer, related persons, offering details).
Workflow:
The script prompts whether you want to retrieve additional data.
If yes, you’ll be asked to input a year (between 2000 and 2013), quarter, month, and day.
It constructs the URL for the SEC EDGAR index, downloads and parses it.
Filters for Form D filings, builds URLs to download the XML filing documents.
Parses each XML file using xml.etree.ElementTree to extract various data points.
Cleans the data and writes the final output to cleaned_data.csv.
How to Run:
Execute the script in a standard Python environment and provide the required inputs when prompted.
Code Structure Overview

Imports & Setup:
Modules such as zipfile, os, pandas, and plotly are imported. The code creates a working directory (extracted_data) and extracts data from Data.zip.
Data Extraction:
Loops over specified years (2014–2024) and quarters (QTR1–QTR4) to load available CSV files, appends metadata, and concatenates the results into a master DataFrame.
Dashboard & Callbacks:
Defines a Dash application (using JupyterDash) with interactive dropdowns, a range slider, and a data table. Callback functions update the table dynamically and enable CSV export.
State-Level Metrics & Visualizations:
Separate code blocks compute metrics (e.g., jurisdiction counts, percentage growth) and generate visualizations (e.g., choropleth maps, line charts) using Plotly.
Interactive Filtering & Column Customization:
Provides command-line functions (versatile_filter and modify_columns) for user-driven data filtering and column selection.
CRM Data Preparation:
Integrates data cleaning, type conversions, and column customization steps. Produces a final CSV file (cleaned_data.csv) formatted for easy CRM import.
SEC EDGAR Data Retrieval & XML Parsing:
Uses SEC EDGAR index files to locate filings, downloads corresponding XML files, and parses them to extract detailed information for further enrichment of the dataset.
Additional Notes

Data Files: Ensure that your Data.zip is correctly formatted (CSV files named <YEAR>_<QUARTER>.csv).
User Input: The dashboard and command-line functions require user interaction. Run them in an environment where you can supply input (Jupyter Notebook or terminal).
User-Agent Header: For SEC EDGAR downloads, update the User-Agent header in the requests if necessary.
CRM Import: The output file cleaned_data.csv is structured to be CRM-ready. Review the selected columns and cleaning steps to ensure compatibility with your specific CRM system.
