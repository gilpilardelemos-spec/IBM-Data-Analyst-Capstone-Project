# IBM-Data-Analyst-Capstone-Project
# Collecting Job Data Using APIs

<p align="center">
    <a href="https://skills.network" target="_blank">
    <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/assets/logos/SN_web_lightmode.png" width="200" alt="Skills Network Logo">
    </a>
</p>

## Estimated Time
**30 minutes**

## Objectives
After completing this lab, you will be able to:

- Collect job data using a Jobs API.
- Store the collected data into an Excel spreadsheet.
- Filter and analyze job postings by technology and location.

> **Note:** Before starting, read all instructions carefully before writing code.

---

## Instructions

1. Open the [Jobs_API notebook](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DA0321EN-SkillsNetwork/labs/module%201/Accessing%20Data%20Using%20APIs/Jobs_API.ipynb).  
   This file contains Flask code required to run the Jobs API.

2. Download the notebook file.

3. Upload the file into your current Jupyter environment using the **Upload** button. Ensure the file is in the same folder as your working notebook.

4. Run all cells in the `Jobs_API` notebook to start the Flask server. Once running, the API will be accessible at the provided URL.

5. (Optional) Learn more about Flask [here](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DA0321EN-SkillsNetwork/labs/module%201/Accessing%20Data%20Using%20APIs/FLASK_API.md.html).

6. After starting the Flask API, you can proceed with this assignment.

---

## Dataset Used

- Original dataset: [Jobs on Naukri.com](https://www.kaggle.com/promptcloud/jobs-on-naukricom) under a **Public Domain license**.
- The lab uses a **modified subset** in JSON format.  
- Keys in the JSON file:
  - Job Title
  - Job Experience Required
  - Key Skills
  - Role Category
  - Location
  - Functional Area
  - Industry
  - Role

> Note: Use the provided dataset for the lab to ensure compatibility with the exercises.

---

## Warm-Up Exercise

The warm-up demonstrates how to access an API. In this example, we fetch data of astronauts currently on the International Space Station (ISS) using:



We print:

- The total number of astronauts.
- The names of each astronaut.

This helps you understand JSON data handling in Python.

---

## Lab: Collect Jobs Data Using Jobs API

### Objective

Determine the number of job postings for various technologies and locations.

### Locations

- Los Angeles
- New York
- San Francisco
- Washington DC
- Seattle
- Austin
- Detroit

### Technologies

- C  
- C#  
- C++  
- Java  
- JavaScript  
- Python  
- Scala  
- Oracle  
- SQL Server  
- MySQL Server  
- PostgreSQL  
- MongoDB  

### Tasks

1. Call the Jobs API and retrieve the full dataset.
2. Write a Python function to find the number of jobs for a given technology.
3. Write a Python function to find the number of jobs for Python in a specific location.
4. Store results in an Excel spreadsheet using `openpyxl`.
5. Save the file as `github-job-postings.xlsx`.

---

## Example Code Snippets

### Import Libraries

```python
import requests
from openpyxl import Workbook
import pandas as pd
wb = Workbook()
ws = wb.active
ws.append(["Technology / Location", "Number of Job Postings"])


def get_number_of_jobs_Python_by_location(location):
    count = 0
    for job in data:
        if "Python" in job['Key Skills'] and location.lower() in job['Location'].lower():
            count += 1
    return location, count

for tech in technologies:
    tech_name, count = get_number_of_jobs_T(tech)
    ws.append([tech_name, count])

locations = ["Los Angeles", "New York", "San Francisco", "Washington DC", "Seattle", "Austin", "Detroit"]
for loc in locations:
    location, count = get_number_of_jobs_Python_by_location(loc)
    ws.append([f"Python in {location}", count])

wb.save("github-job-postings.xlsx")
