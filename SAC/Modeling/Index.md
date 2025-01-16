# Modeling

There are four types of models in SAC. It is used for stories(read) and planning(read/write).

# 1. Datasets

They represent the simple tables with semantic.

See the difference in this [link](https://help.sap.com/docs/SAP_ANALYTICS_CLOUD/00f68c2e08b941f081002fd3691d86a7/05280d13b16e40f3be37165e9755d84b.html)


# 2. Modeler

You can create Model and then create public dimesion tables inside the model or create dimension table first and add it into the model.

![alt text](/Admin/images/Space.png)

The dimension table is different from dimension(attribute) as in SAP BW. There are special types dimensions and "generic" type dimenions, which is like the text attribute as in SAP BW.

These types dimension tables are mainly used for **Planning**
- Account
- Organizaion

[!important ]
Dimension = Field
Member = Value

## 2.1 Creating Models by importing Data

![alt text](/Admin/images/Space.png)
After importing the data and save the model, you can begin to transfer the data.

![alt text](/Admin/images/Space.png)
You can view the data and modify the data by using the formulas.

![alt text](/Admin/images/Space.png)
You can convert the field(dimension) to property like text or hierarchy.

Now you can explore the data in xxx.
![alt text](/Admin/images/Space.png)

# 2.2. Creating Model from LiveConnection

![alt text](/Admin/images/Space.png)

Connec to the datashpere and consume the data from the Analytic Model 

# 3. Planning Model

Version (default and must)
Account
Organization (for currency conversion)

# 4. Embedded Model



