# Exploratory-Data-Analysis

# Install the required library

import micropip
await micropip.install('pandas')

# Import pandas after installation

import pandas as pd
print(pd.__version__)

# Load the dataset
from pyodide.http import pyfetch
async def download(url, filename):
    response = await pyfetch(url)
    if response.status == 200:
        with open(filename, "wb") as f:
            f.write(await response.bytes())

# Define a file path

file_path = "https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/n01PQ9pSmiRX6520flujwQ/survey-data.csv"

# Download the file

await download(file_path, "survey_data.csv")
file_name="survey_data.csv"

# Load the data

df = pd.read_csv(file_name)

# Display the top 5 rows and columns from your dataset.

df.head(5)

# Print the datatype of all columns.

df.dtypes

# Print the mean age of the survey participants.

df["Age"].mean()

# Print how many unique countries are there in the Country column.

h = df['Country'].value_counts()
h
h.nunique()
