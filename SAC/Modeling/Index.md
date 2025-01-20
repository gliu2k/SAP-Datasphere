# Modeling

There are four types of models in SAC. They are used in stories(read) and planning(read/write).

# 1. Datasets

They represent the simple tables without semantic.

See the difference in this [link](https://help.sap.com/docs/SAP_ANALYTICS_CLOUD/00f68c2e08b941f081002fd3691d86a7/05280d13b16e40f3be37165e9755d84b.html)


# 2. Modeler

You can create Model and then create public dimesion tables inside the model or create dimension table first and add it into the model.

![alt text](/SAC/Modeling/images/NM1.png)

The dimension table is different from dimension(attribute) as in SAP BW. There are special types dimensions and "generic" type dimenions, which is like the text attribute as in SAP BW.

> [!IMPORTANT]
>  Different concepts in SAC.
> 
> Dimension(SAC) = Field(Table) + Property
> 
> Member(SAC) = Value(Table)

These types dimension tables are mainly used for **Planning**.
- Account
- Organizaion
- Date (default)
- Version (default)

The **conversions** is for the currency conversion tables created manually or imported from BPC.

## 2.1. Creating Models by importing Data

1. We can import the data from differetn data sources.

![alt text](/SAC/Modeling/images/NM2.png)

2. After importing the data and saving the model, we can begin to transform(modify) the data.
![alt text](/SAC/Modeling/images/TR1.png)

3. We can view the data and modify the data by using the formulas.
![alt text](/SAC/Modeling/images/TR2.png)

4. We can also convert the field(dimension) to the property of other dimension like text or hierarchy.
![alt text](/SAC/Modeling/images/NM3.png)

5. We can set up the **Data Access Control**.
![alt text](/SAC/Modeling/images/DAC.png)

6. Everything is done. We can now explore the data of the model in **Data Analyzer**.
![alt text](/SAC/Modeling/images/DE.png)

## 2.2. Creating Empty Models 
We can create an empty model and then import the data.  It will be covered in the **Planning** section.

> [!Note]
>  It is more flexiable and is the best practise.

## 2.3. Creating Model from LiveConnection

![alt text](/SAC/Modeling/images/NM4.png)

The LiveConnection to SAP HANA/BW system does now work in SAC trial version.

# 3. Planning Model
The structure of planning model is similar to the analytic model.

Theare are special features. All details are covered in **Planning** section. 

- Version(Category): budget/plan/forecast
- Audit Function
- Authorization Control to control data visibility
  
# 4. Embedded Model
It is part of story and can only be used with it.

# 5. Currency Conversion
1. Create the currency conversion table (source/target/rate/time)
2. Turn on the currency conversion setting in hte model
3. Create the currency variable in the model or calculation measure in the story

See the details [here](https://learning.sap.com/learning-journeys/leveraging-sap-analytics-cloud-functionality-for-enterprise-planning/configuring-currency-translation_ce44b7c8-5020-44c0-94b2-b54b68ec5d92)


