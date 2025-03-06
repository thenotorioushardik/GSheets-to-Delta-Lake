# GSheets to Delta Lake

## Overview
This script automates the extraction of data from Google Sheets and loads it into Delta Lake tables within Databricks. The script leverages **PySpark**, **Pandas**, and **Google Sheets API** to fetch, process, and store structured data efficiently.

## Features
- **Automated Data Extraction**: Reads data from multiple Google Sheets using the Google Sheets API.
- **Schema Handling**: Renames duplicate columns to maintain data integrity.
- **Data Transformation**: Converts Google Sheets data into a structured Pandas DataFrame before loading it into PySpark.
- **Delta Lake Storage**: Writes processed data into **Delta Tables** within Databricks for scalable and optimised querying.
- **Secure Access**: Uses OAuth2-based authentication.

## Tech Stack
- **PySpark** (for distributed data processing)
- **Pandas** (for DataFrame manipulations)
- **Google Sheets API** (for data retrieval)
- **Databricks Delta Lake** (for storage and querying)
- **gspread & oauth2client** (for Google Sheets authentication)

## Installation
### Prerequisites
Ensure you have the following installed:
- Python 3.x
- PySpark
- Pandas
- gspread
- oauth2client

You can install the required dependencies using:
```sh
pip install pyspark pandas gspread oauth2client
```

## Google Authentication Setup
To connect to Google Sheets API, follow these steps:
1. Go to the [Google Cloud Console](https://console.cloud.google.com/).
2. Create a new project and enable the **Google Sheets API** and **Google Drive API**.
3. Go to **Credentials** and create a new **Service Account**.
4. Generate a JSON key and download it.
5. Share your Google Sheet with the service account email (ending in `gserviceaccount.com`) with **Editor** access.
6. Store the JSON key securely and reference it in your script for authentication.

## Usage
1. **Set Up Google API Credentials**
   - Obtain a Google service account JSON key.
   - Store it securely and load it within the script (ensure sensitive details are excluded from public repositories).

2. **Define Sheet Mappings**
   - Update the `sheets_data` list with relevant Google Sheet URLs (keep links up to the **edit** part, without `gid`), worksheet names, and Delta Table names.

   Example:
   ```python
   sheets_data = [
       {
           "sheet_url": "YOUR_GOOGLE_SHEET_URL_1",
           "worksheet_name": "YOUR_WORKSHEET_NAME_1",
           "table_name": "YOUR_DELTA_TABLE_NAME_1"
       },
       {
           "sheet_url": "YOUR_GOOGLE_SHEET_URL_2",
           "worksheet_name": "YOUR_WORKSHEET_NAME_2",
           "table_name": "YOUR_DELTA_TABLE_NAME_2"
       }
   ]
   ```

## Troubleshooting
- **Authentication Errors**: Ensure the service account JSON file is valid and correctly referenced.
- **Google Sheets Access Denied**: Verify that the service account has been granted editor access to the sheets.
- **Delta Table Not Found**: Ensure Databricks workspace is configured correctly.

## Contributing
Contributions are welcome! If you find any issues or have suggestions for improvement, feel free to fork the repository and submit a pull request.
