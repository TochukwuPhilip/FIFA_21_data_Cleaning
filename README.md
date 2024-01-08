# FIFA_21_data_Cleaning

![image](https://github.com/TochukwuPhilip/FIFA_21_data_Cleaning/assets/108484860/9cd0a871-65ef-4713-81df-32904a51acbe)

# Introduction

Data cleaning is the process of fixing or removing incorrect, corrupted, incorrectly formatted, duplicate, or incomplete data within a dataset.
![image](https://github.com/TochukwuPhilip/FIFA_21_data_Cleaning/assets/108484860/56bebc02-f85e-49e6-8316-593b094ca4ca)

This project is a data cleaning task that is used to demontrate my ability to clean a dataset using the Power BI's Power Query. 

# Objective and Problem Statement

The main purpose of this approach is to eliminate the following occurrences to ensure reliable and accurate data for further analysis.
- Correcting Inaccuracies and Errors
- Standardizing and Transforming Data
- Handling Special Characters and Encoding Issues
- Handling Inconsistent Formats

# Description of the FIFA 21 Dataset

This FIFA 2021 dataset was sourced from [Kaggle](https://www.kaggle.com/datasets/yagunnersya/fifa-21-messy-raw-dataset-for-cleaning-exploring/).
The raw dataset was scraped from sofifa.com, containing 18,979 players and 77 data points on their performance. It comes with a handy guide to decipher player info. 
The columns in the dataset includes ID, Name, Long Name, photo URL, player URL, Nationality, Age, OVA, POT, Contract, Positions, Height, Preferred Foot, BOV, Best Position, Joined, Loan Date End, Value, Wage, Release Clause, W/F, SM, A/W, D/W, IR, PAS, DRI.
Join me as I employ Power Query to clean this data, transforming it from messy to analysis-ready, step-by-step.

# Data Cleaning Process

The data is imported into Power Bi using the "get data" function under the data ribbon.

![image](https://github.com/TochukwuPhilip/FIFA_21_data_Cleaning/assets/108484860/65c0b9c6-ef03-493d-a36b-bcf3be15e8f4)

Selecting the data from it's location on my local machine gives two options: loading the data immediately or selecting the "Transform data" option.
I select the transform data option as this would enable me to perform data cleaning on the FIFA dataset.

![image](https://github.com/TochukwuPhilip/FIFA_21_data_Cleaning/assets/108484860/018af449-8f32-48d9-8630-b9c57b16f0a6)

The above shows how the dataset looks like in the power query. Also, the column quality option was selected under the view menu in order to see the percentage of valid data, errors and empty cells within each of the 77 columns of the dataset.

## ID, Name, LongName, photoUrl and playerUrl Columns

The ID column is the Players' identification number.  This is unique for each player. The column is 100% valid and has no errors nor empty cells.
The Name column is the short name of the players while the LongName column contains the full names of the players. I will remove the Name column and retain the LongName column since it contains full names
The photoUrl and the playerUrl columns are 100% valid and have no errors nor empty cells. These cells formats are consistent and shall be retained in the dataset.

![image](https://github.com/TochukwuPhilip/FIFA_21_data_Cleaning/assets/108484860/921cb843-b12e-4c2e-8add-b45556c3318c)

The ID column has been renamed as Player_id, while the  LongName column has been renamed as Full_name

![image](https://github.com/TochukwuPhilip/FIFA_21_data_Cleaning/assets/108484860/dfec7ee9-8ae3-4690-b879-5b5b79c8bc7f)

## Nationality, Age, OVA, POT and Club Columns

![image](https://github.com/TochukwuPhilip/FIFA_21_data_Cleaning/assets/108484860/643ab875-6a54-498b-ab3c-35f0f08d5636)

The Nationality column shows country or originality of players. It is complete and consistent.
The Age column consist of players' age. This is also complete and consistent.
OVA(Overall Rating Analysis) consists of player’s perceived or evaluated skills and abilities. The column has been renamed as Overall_rating. The POT(Potential) column refers to a player’s perceived ability to develop into a better player over time. The column has been renamed as Potential.
The club column has some inconsistent naming formats. Some clubs have prefixes which should be removed in order to make them consistent with other naming club's naming formats.

![image](https://github.com/TochukwuPhilip/FIFA_21_data_Cleaning/assets/108484860/060e1ecf-6c80-4067-b290-6df0b814fe41)

I have used the "Replace values" function to correct the irregularity.

![image](https://github.com/TochukwuPhilip/FIFA_21_data_Cleaning/assets/108484860/2802c9f8-f943-4e78-a626-70c3c0f9c85f)












