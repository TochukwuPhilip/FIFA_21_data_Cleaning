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

## Contract and Position columns
![image](https://github.com/TochukwuPhilip/FIFA_21_data_Cleaning/assets/108484860/cffd9081-2f80-4cc3-8548-c703c9fcb498)

Ontract column: Filtering the column shows that the column contains inconsistent data as follows:

![image](https://github.com/TochukwuPhilip/FIFA_21_data_Cleaning/assets/108484860/9aebbb54-8bf9-4685-8384-c6bb2af2e823)

The contract column values show three categories of data, a year range (e.g, 2020 ~ 2024), "free" and "... loan" types.
First, I used the "replace value" function to change the "~" character to "-".

![image](https://github.com/TochukwuPhilip/FIFA_21_data_Cleaning/assets/108484860/24e53834-1658-42fd-9e4d-31834fa1b3c6)

Second, I created a conditional column to identify the three categories of contract as "Contract", "Free" and "Loan"
If the contract column contains "-" return "Contract"
Else if if contract contains "free", return "Free"
Else return "Loan"
= Table.AddColumn(#"Replaced Value1", "Contract_type", each if Text.Contains([Contract], "-") then "Contract" else if [Contract] = "Free" then "Free" else "Loan")

![image](https://github.com/TochukwuPhilip/FIFA_21_data_Cleaning/assets/108484860/4050bcf2-e09e-4ce4-803c-26ab2c2a8e1e)

![image](https://github.com/TochukwuPhilip/FIFA_21_data_Cleaning/assets/108484860/4b94d043-b2fe-40f7-8499-7597c22f2952)

## Deriving the Contract Duration Column
The contract duration column has been derived by splitting the Contract column into two and using custom column to find the difference between them

![image](https://github.com/TochukwuPhilip/FIFA_21_data_Cleaning/assets/108484860/cfaa514e-1e24-48d6-8c03-e9b1bc1ff04a)

![image](https://github.com/TochukwuPhilip/FIFA_21_data_Cleaning/assets/108484860/d8ef586c-a1c7-4095-b27e-cfd814f1e743)

## Height and Weight Columns
The Height and weight columns consist of inconsistent values.
The height column has measurements in cm and feet while the Weight column has measurements in lb and kgs.
The following formula has been used to convert ft to cm:
New_height = 
    Table.AddColumn(
        Table.SelectRows(#"PreviousStep", each not Text.Contains([Height], "cm")),
        "New_height", 
        each Number.From(
            Text.Start(
                [Height], 
                Text.PositionOf([Height], "'") - 1
            )
        ) * 30.48 + Number.From(
            Text.Range(
                [Height], 
                Text.PositionOf([Height], "'") + 1, 
                Text.PositionOf([Height], """") - Text.PositionOf([Height], "'") - 1
            )
        ) * 2.54
    )
New_weight = Table.AddColumn(#"PreviousStep", "New_weight", each
    if Text.Contains([weight], "kg") then
        Number.From(Text.Start([weight], Text.PositionOf([weight], "kg") - 1)) * 2 - 20
    else
        Number.From(Text.Start([weight], Text.PositionOf([weight], "lbs") - 1))
)
![image](https://github.com/TochukwuPhilip/FIFA_21_data_Cleaning/assets/108484860/2a8caba4-7193-4065-a24d-c34a05b924a9)

## Value, Wage and Release Clause Column

![image](https://github.com/TochukwuPhilip/FIFA_21_data_Cleaning/assets/108484860/a1a3ba2c-cf26-4185-9162-89b0b3c8dcaa)

These columns were written in thousand (K) and millions(M) and have the euro sign in every cell.The prefixes and suffixes have been removed. Where M is for millions, ‘K’ for thousands and ‘€’ for euro.
A conditional column "value by K or M" was created to multiply the values with ‘K’ by 1000 and values with ‘M’ by 1000000.
Next, the "Value" column in is tripped of letters "M" and "K" while the column is converted to whole number data type.

A custom column is created to find the product of the "value" column and the "value by K or M" column to find the "value_amt"
![image](https://github.com/TochukwuPhilip/FIFA_21_data_Cleaning/assets/108484860/4403d3b8-cb2c-4b3b-b910-f6613634378e)

These steps are repeated for "Wage" and "Release Clause" columns.

## Other Columns
The rest of the columns in the dataset have been observed for consistency, errors, empty cells, irregular/inconsistent formats, special characters and outliers.

# Summary and Conclusion
Data cleaning is a very important skill in the arsenal of the data practitioner. 
The Power BI tool has been utilized during this task to wrangle or clean the data to make it ready for further analysis.

Having carried out a thorough observation, identifying and rectifying Inaccuracies and Errors, Standardizing and Transforming Data,Handling Special Characters and Encoding Issues, Handling Inconsistent Formats,  the messy dataset is now clean and ready to be used for analysis.
Carrying out this task has exposed me to real-life scenarios on how to handle messy data and prepare it for for analysis, as a messy and inconsistent data format can deter meaning ful analysis and lead to erroneous conclusions.

















