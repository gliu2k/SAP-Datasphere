# Planning

# 1. Model

![alt text](/SAC/Planning/images/PM1.png)

1. Create an empty model with three types of dimensions

- Accounts
- Organization - Used for currency
- Generic
- Version - created automatically by default

2. Add the master data into the dimension tables manually

3. Perform dimension mapping and load the actual and planning data (option) from the flat files into model
   
4. Set up the planning model 

> [!Important]
> The master data and the actual transactation data in **Step2** and **Step3** can be loaded from Datasphere via OData connection. We can load the history planning data via flat file as in **Step2**.


# 2. Planning 
![alt text](/SAC/Planning/images/DP1.png)

1. Add the planning model in Story/Canvas
2. Copy the Forecast version data into Private vesion
3. Perform planning manually in the cell

![alt text](/SAC/Planning/images/DP2.png)

> [!Tip]
> Use the **distribut value** or **Allocation** (Menu Tools...) to fasten the process.

# 3. Planning Flows
We can use **Data Action(Steps)** to create planning flow to achieve

- Copy
- Allocation
- Conversion
- Others

# 4. Value Drive Tree

This is the tool to do planning simualation during the planning.

# 5. Authoriztion

This is very critical duirng planning

Locks:

To be added...
