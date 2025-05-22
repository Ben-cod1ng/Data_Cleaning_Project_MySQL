# Data_Cleaning_Project_MySQL
This Project gives you a detailed process on how to do data cleaning on a massive dataset in MySQL.
# Layoff Data Cleaning Project (MySQL)

## Overview

This project demonstrates the process of cleaning a raw layoffs dataset using MySQL. It walks through essential data cleaning steps such as removing duplicates, standardizing values, handling missing data (NULLs), and formatting dates. This is useful for preparing data for analysis or reporting in real-world data projects.

---

## Dataset

The original dataset (`layoffs`) contains company layoff information, including fields like:
- `company`
- `location`
- `industry`
- `total_laid_off`
- `percentage_laid_off`
- `date`
- `stage`
- `country`
- `funds_raised_millions`

---

## Steps Performed

### 1. **Database Setup**
- Created a database: `data_cleaning_project`
- Created a staging table: `layoffs_staging` as a clone of the original `layoffs` table
- Copied data into `layoffs_staging` for cleaning

### 2. **Removing Duplicates**
- Used `ROW_NUMBER()` and `PARTITION BY` to identify duplicate records
- Created a second staging table `layoffs_staging2` with a `row_num` column
- Deleted all records where `row_num > 1` to eliminate duplicates

### 3. **Standardizing Data**
- Trimmed whitespace from text columns (e.g., `company`)
- Standardized values (e.g., replaced all `Cryptocurrency` entries with `Crypto`)
- Cleaned up country names (e.g., removed trailing periods)
- Converted the `date` column from string to actual `DATE` type

### 4. **Handling NULLs**
- Identified rows with missing `total_laid_off` and `percentage_laid_off`
- Replaced empty string entries in `industry` with `NULL`
- Used `JOIN` operations to fill missing `industry` values based on matching `company` data

### 5. **Final Cleanup**
- Deleted rows where both `total_laid_off` and `percentage_laid_off` are `NULL`
- Dropped the `row_num` helper column after cleaning was complete

---

## Technologies Used

- MySQL 8.0
- SQL (DDL & DML)
- MySQL Workbench

---

## How to Use

1. Clone this repository
2. Open MySQL Workbench or any compatible SQL editor
3. Execute the SQL script provided in chunks to see the step-by-step cleaning process
4. Use the cleaned `layoffs_staging2` table for your analysis or reporting

---

## Author

*Karikari Benjamin*  
*GitHub: [your-username](https://github.com/Ben-cod1ng)*

---

## License

This project is licensed under the MIT License.

