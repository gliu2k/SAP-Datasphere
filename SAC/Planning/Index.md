# Planning

# 1. Model

![alt text](/SAC/Planning/images/PM1.png)

1. Create an empty model with three types of dimensions

- Account
- Organization - used for currency
- Generic
- Version - created automatically by default

2. Add the master data into the dimension tables manually

4. Perform dimension mapping and load the actual and planning data (option) from the flat files into model
![alt text](/SAC/Planning/images/PM2.png)

> [!Important]
> The master data and the actual transactation data in **Step2** and **Step3** can be loaded from Datasphere via OData connection. We can load the history planning data via flat file as in **Step2**.
>
> But, if you do want to write the planning data into ACDOCP table. Maybe you need to consider implementing BPC or find a workaround.

5. Set up the planning model

6. Check the loaded data in **Data Analyzer**

![alt text](/SAC/Planning/images/PM3.png)

I used the **COPY** action to copy the actual data of 2023Q3 and 2023Q4 to 2024Q3 and 2024Q4 respectively because they are missing in the orignal dataset(flat files).

# 2. Planning 
1. Create **Data Actions** to copy the **2024Q4** Forecast version data to to **2025Q1**
![alt text](/SAC/Planning/images/DP1.png)

2. Add the planning model into Story/Canvas
![alt text](/SAC/Planning/images/DP2.png)

3. Copy the **Forecast** version data into **Private Forecast** version
![alt text](/SAC/Planning/images/DP3.png)

4. Perform planning manually in the cell
![alt text](/SAC/Planning/images/DP4.png)

> [!Tip]
> Use the **Distribut value** or **Allocation** (Menu Tools...) to fasten the process.

# 3. Planning Functions

## 3.1. 
- Distribut value
- Allocation
- Grid Pages

## 3.2. Data Actions
- Copy
- Allocation
- Others
  
# 3.3. Value Drive Tree
This is the tool to do planning simualation during the planning.

# 3.4. Publish
# 3.5. Version Control

# 5. Authoriztion

This is very critical duirng planning

Locks:

To be added...
