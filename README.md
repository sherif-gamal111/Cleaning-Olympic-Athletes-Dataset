# Cleaning-Olympic-Athletes-Dataset

## Overview
This project involves cleaning and transforming a large dataset of Olympic athletes containing 145,500 rows of raw biographical data. The original dataset was messy, containing inconsistent formatting, embedded information within columns, and various data quality issues that needed to be resolved for meaningful analysis.

---
## Dataset Source
The data was sourced from the Olympics Dataset repository and includes biographical information about athletes who have participated in the Olympic Games.

---
## Data Cleaning Process
### 1. Column Standardization
Sex Column: Verified all values are either "Male" or "Female" with no null values

Used Name Column: Renamed to "Name" and removed the • delimiter, replacing it with spaces

### 2. Birth Information Parsing
The original Born column contained combined date and location information formatted as:
"12 December 1886 in Bordeaux, Gironde (FRA)"

Transformations applied:

Replaced "in" and "(" with commas, removed ")"

Split into four separate columns:

Born date (converted to datetime type)

Born city

Born region

Born country

Cleaned up entries with approximate dates (circa, c., etc.)

### 3. Death Information Parsing
Applied the same transformation logic to the Died column, creating:

Died date (datetime type)

Died city

Died region

Died country

### 4. Measurements Processing
The Measurements column originally contained values like:

"183 cm / 76 kg"

"178 cm"

"120 kg"

Transformations applied:

Split into Height_cm and Weight_kg columns

Removed "cm" and "kg" suffixes for numeric data

Handled cases where measurements only contained height or weight

Cleaned entries with multiple values (ranges or commas)

### 5. Data Validation
Verified all athlete IDs are non-null

Counted and handled null values appropriately

Removed duplicate entries (if any)

---
## Final Dataset Structure
| Column | Description | Data Type |
| ------ | ----------- | --------- |
| athlete_id | Unique identifier for each athlete | Integer |
| Name | Athlete's name (cleaned) | String |
| Height_cm | Height in centimeters | Integer/Float |
| Weight_kg | Weight in kilograms | Integer/Float |
| Born date | Date of birth (ISO format) | Datetime |
| Born city | City of birth | String |
| Born region | Region/state of birth | String |
| Born country | Country code of birth (3-letter) | String |
| Died date | Date of death (ISO format) | Datetime |
| Died city | City of death | String |
| Died region | Region/state of death | String |
| Died country | Country code of death (3-letter) | String |

---
## Files in Repository
Cleaning-Olympic-Athletes.ipynb - Jupyter notebook containing the complete data cleaning process

Cleaned Data.csv - The final cleaned dataset ready for analysis

README.md - Project documentation

---
## Technologies Used
Python 3.13

Pandas - Data manipulation and cleaning

NumPy - Handling null values and numerical operations

Jupyter Notebook - Interactive development environment

---
## Key Cleaning Operations Performed
1. String manipulation: Removed special characters, standardized delimiters

2. Column splitting: Parsed combined information into logical separate columns

3. Data type conversion: Converted date strings to datetime objects

4. Null value handling: Identified and appropriately marked missing data

5. Pattern matching: Used regex patterns to identify and clean irregular entries

6. Data validation: Ensured data consistency across all records

---
## Sample Data (Before vs After)
Before:

| Used name | Born | Measurements |
| --------- | ---- | ------------ |
| Jean-François•Blanchy | 12 December 1886 in Bordeaux, Gironde (FRA) | NaN |

After:

| Name | Born date | Born city | Born region | Born country |
| ---- | --------- | --------- | ----------- | ------------ |
| Jean-François Blanchy | 1886-12-12 | Bordeaux | Gironde | FRA |

---
## Usage
To load the cleaned dataset for analysis:

```python
import pandas as pd

df = pd.read_csv('Cleaned Data.csv')
df['Born date'] = pd.to_datetime(df['Born date'])
df['Died date'] = pd.to_datetime(df['Died date'])
```

---
## 🌟 About Me

Hi, I’m Sherif, a Data Engineer with a strong foundation in Industrial Engineering and specialized in Data Engineering.
I hold a Bachelor of Engineering (BEng) in Industrial Engineering from Canadian International College (CIC) and a Microsoft Data Engineering degree from Digital Egypt Pioneers Initiative (DEPI).
I am fascinated by how systems work, how processes can be optimized, and how the right information at the right time can change everything. That curiosity led me to Industrial Engineering, and later, to Data Engineering.

Let's stay in touch! Feel free to connect with me on the following platforms:

[Gmail](sherif.gamal.kamel121@gmail.com)
[LinkedIn](https://www.linkedin.com/in/sherifgamalkamel)
[Upwork](https://www.upwork.com/freelancers/~01b7b6e3cdf572d79e)
[Freelancer](https://www.freelancer.com/u/SherifGamal5)
[Portfolio](https://sherif-gamal-data-engine-ns2r13f.gamma.site/)
