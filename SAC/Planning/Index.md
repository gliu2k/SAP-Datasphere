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

6. Check the loaded forecast and actual versions data in **Data Analyzer**

![alt text](/SAC/Planning/images/PM3.png)

I used the **COPY** action to copy the actual data of 2023Q3 and 2023Q4 to 2024Q3 and 2024Q4 respectively because they are missing in the original dataset(flat files).

# 2. Planning 
1. Create **Data Actions** to copy the **2024Q4** Forecast version data to to **2025Q1**
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

6. In the story **View** mode, choose **Publish**, the planning data made by the user in the **Private** forecast version will be copied to the **puliic** forecast version.
 
# 3. Planning Functions

## 3.1. Simple
- Distribute value
- Allocation
- Grid Pages (depreicate)

## 3.2. Data Actions

This is the action I used to do the version copy.
![alt text](/SAC/Planning/images/DA1.png)
You can define the actions(steps) and run them in sequence in the Canvas(Stories). If one step fails, the whole process will get reversed just as the transaction in database.

![alt text](/SAC/Planning/images/DA2.png)

**Step Types:**
- Copy
- Allocation
- Embeded Data
- Conversion
- Advanced Formulas

## 3.3. Multi Actions
To be added...

## 3.4. Value Drive Tree
This tool can be used to do simualation during the planning.
![alt text](/SAC/Planning/images/VDT.png)

# 4. Locks
This is very critical duirng planning.

To be added...

# 5. Calendar
To be added...
