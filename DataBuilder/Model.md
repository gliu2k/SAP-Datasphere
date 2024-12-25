# Data Builder

In fact, it contains not only the model components but also the ETL elements.In this section, I will focus on the data modeling part.
![alt text](/DataBuilder/images/DataBuilder.png?raw=true)


## Tables

![alt text](/DataBuilder/images/Tables.png?raw=true)

You can create the local tables, generate a local table by importing CSV file, or import remote tables. 

> [!NOTE]
> Remote tables: virtual table as in HANA-SDA or the “link”, as in **Azure Fabirc**, which maps to the physical object locating in the remote system.


### 1. Semantic Usage:
![alt text](/DataBuilder/images/NewTable.png?raw=true)

> [!IMPORTANT] 
> -	**Fact**: Transaction Data and the only type can be used in creating Analyitc Model
> -	**Dimension/Text/Hiearchy**: master data and are used in the assiciation of fact, view or other dimension tables 

### 2. Assocation: 
![alt text](/DataBuilder/images/TableAssoication.png?raw=true)
Define the attributes/text of the data field



### 3. Delta Capture
![alt text](/DataBuilder/images/TableDelta.png?raw=true)

> [!IMPORTANT] 
> - Two local tables, the active and the detla table("technicalname_Delta") are generated when the “Delat Capture” flag is turned on. 
> - Two additional fields, "Change Type" and "Change Datae" are included in the "delta" table,. The "Change Type" can have value of "I"(initial), "D"(delete) and "U"(updated) in the same record after certain acitivy take place.


## Views
There are two types of views, SQL View and Graphics View, in datasphere. Both are the virtual objects. 

![alt text](/DataBuilder/images/Views.png?raw=true)

### SQL View
It supports SQL and SQLScript(**table function**). The latter is the same as the table function used in AMDP or ABAP CDS View.

### Graphic View
It is similar to the HANA Calculation View. It is optimized and has better performance.

![alt text](/DataBuilder/images/NewGV.png?raw=true)

> [!IMPORTANT]
>-	It has "semamtic type" as well. And, only the fact one can be used in the Analytic Model.
>-	The "attributes" are the same as "columns" defined in HANA view
>-  The attribute can have "association" too.
>-	It has "Input Parameter", as same as in HANA view. It should be pushed to lower node in order to get better performance and be mapped to the variable created in the upper layer like Analytic Model.
>-  Join, UNION, Filter and projection(show/hide columns), Aggretion Node are the same as in HANA view.
>-  Data preview is avaialbe in each node.

## ER Model
It is used to display the detailed information in the object so that we can have a good understanding about the design of a model.

![alt text](/DataBuilder/images/ERModel.png?raw=true)


## Analytic Models

![alt text](/DataBuilder/images/NewGV.png?raw=true)

[Introducing the Analytic Model in SAP Datasphere](https://community.sap.com/t5/technology-blogs-by-sap/introducing-the-analytic-model-in-sap-datasphere/ba-p/13568591)

## Currency Conviersion View
![alt text](/images/NewGV.png?raw=true)

## Data Access
![alt text](/images/NewGV.png?raw=true)

[Privieage]()
[datga Access ]https://community.sap.com/t5/technology-blogs-by-sap/sap-datasphere-security-amp-data-access-controls-overview/ba-p/13805353



