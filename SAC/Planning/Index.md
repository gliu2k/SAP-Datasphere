# Planning

# 1. Model

![alt text](/SAC/Planning/images/PM1.png)

1. Create an empty model with four types of dimensions

- Account
- Organization - used for currency
- Generic
- Version - created automatically by default

2. Add the master data into the dimension tables manually

3. Perform dimensions mapping and load the actual and planning transaction data (optional) from the flat files into model
![alt text](/SAC/Planning/images/PM2.png)

> [!Important]
> The master data and the actual transactation data in **Step2** and **Step3** can be loaded from Datasphere via OData connection. We can load the historical planning data via flat file as in **Step2**.
>
> But, if you do want to write the planning data into ACDOCP table. Maybe you need to consider implementing BPC or the approach in this [article](https://www.linkedin.com/pulse/exporting-sac-planning-data-sap-s4-hana-aricordconsultinglimited-je1ie/)

4. Create **Validation Rule**(optional)
   
- It is used to ensure that valid combinations of the entities. See the details in this [blog](https://community.sap.com/t5/technology-blogs-by-members/sap-analytics-cloud-planning-validation-rules/ba-p/13475166)

5. Set up the planning model

6. Check the loaded forecast and actual versions data in **Data Analyzer**
![alt text](/SAC/Planning/images/PM3.png)

> [!Note]
> There are no actual(version) data of 2024Q3 and 2024Q4 in the original dataset(flat files).
> Therefore, I used the **Copy - Data Action** to copy the actual data of 2023Q3 and 2023Q4 to 2024Q3 and 2024Q4 respectively. You can see that they are identical.

# 2. Planning 
1. Create **Data Actions** to copy the **2024Q4** Forecast version data to to **2025Q1** and set up the locks which are covered in the below **Data Locking** section.
![alt text](/SAC/Planning/images/DP1.png)

2. Add the planning model into Story/Canvas and copy the 2025Q1 data from the **Forecast** version to **Private Forecast** version
![alt text](/SAC/Planning/images/DP3.png)

3. Perform planning on the **Private Forecast 2025Q1** version manually in the table cell
![alt text](/SAC/Planning/images/DP4.png)

> [!Tip]
> Use the **Distribute value** or **Allocation** (Menu Tools...) to fasten the process.

4. Use **Distribute value** to distribue 2025Q1 data to P01, P02, P03 evenly.
![alt text](/SAC/Planning/images/DP5_Dist.png)

5. Two ways to reverse the changes - **Undo** butoon or back to the step in the version history
![alt text](/SAC/Planning/images/DP6_Rev.png)

6. In the story **View** mode, choose **Publish**, the planning data made by the user in the **Private** forecast version will be copied to the **public** forecast version.
 
# 3. Planning Functions

## 3.1. Manual Input
- Distribute value
- Allocation
- Grid Pages (Deprecated)

## 3.2. Data Actions

This is the action I used to do the version copy.
![alt text](/SAC/Planning/images/DA1.png)
You can define the actions(steps) and run them in sequence in the Canvas(Stories). If one step fails, the whole process will get reversed just as the transaction in database.

![alt text](/SAC/Planning/images/DA2.png)

**Action Step Types:**
- Copy
- Allocation
- Embeded Data
- Conversion
- Advanced Formulas

**Advanced Formulas is very powerful**.
![alt text](/SAC/Planning/images/DA3.png) 

## 3.3. Multi Actions

They are:
- Data Action
- Predictive
- Version Management
- Data Locking
- Data Import
- API

![alt text](/SAC/Planning/images/MA1.png)

> [!Note]
> Different from **Data Actions**, the data action steps defined here are executed indepently(not one fails all rollback).
>
> The jobs for data import are STEP2 and STEP3 in **Model** section above. 

See details in this [blog](https://assets.sapanalytics.cloud/production/help/help-release/en/a8435da6970041d2beb3299cdcff7026.html#loioa8435da6970041d2beb3299cdcff7026)

## 3.4. Value Drive Tree
This tool can be used to do simualation during the planning.
![alt text](/SAC/Planning/images/VDT.png)

# 4. Data Locking
This is a very **critical** step during planning. 

Before starting the planning procedure, we must assign the ownership to the data(cells) and lock all the cells.
![alt text](/SAC/Planning/images/LOCK1.png)

Only the owners, like the CIOs or IT managers in this case, can unlock the data/cells and do the data forecasting on the IT expense.
![alt text](/SAC/Planning/images/LOCK2.png)

# 5. Calendar
All the **Jobs** for the data(either master or transaction) loading and **Data Actions** can be grouped and scheduled in **Calendar**.

They can be scheduled or triggered on events.

![alt text](/SAC/Planning/images/C1.png)
