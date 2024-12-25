# Data Builder

In fact, it contains not only the model components but also the ETL elements. In this section, I will focus on the data modeling part.

![alt text](/DataBuilder/images/DataBuilder.png?raw=true)


## 1. Tables

![alt text](/DataBuilder/images/Tables.png?raw=true)

You can create the local tables, generate a local table by importing CSV file, or import remote tables. 

> [!NOTE]
> Remote tables: virtual table as in HANA-SDA or the “link”, as in **Azure Fabric**, which maps to the physical object locating in the remote system.


### 1.1. Semantic Usage
![alt text](/DataBuilder/images/NewTable.png?raw=true)

> [!IMPORTANT] 
> -	**Fact**: Transaction Data and the only type can be used in creating Analytic Model
> -	**Dimension/Text/Hierarchy**: master data and are used in the association of fact, view or other dimension tables 

### 1.2. Association
Add the attributes/text to the field.

![alt text](/DataBuilder/images/TableAssociation.png?raw=true)


### 1.3. Delta Capture
![alt text](/DataBuilder/images/TableDelta.png?raw=true)

> [!IMPORTANT] 
> - Two local tables, the active and the detla table("Technicalname_Delta") are generated when the “Delat Capture” flag is turned on. 
> - Two additional fields, "Change Type" and "Change Datae" are included in the "delta" table. The "Change Type" can have value of "I"(initial), "D"(delete) and "U"(updated) in the same record after certain activity takes place.


## 2. Views
There are two types of views, SQL View and Graphics View, in datasphere. Both are virtual objects. <BR/>

![alt text](/DataBuilder/images/Views.png?raw=true)

### 2.1. SQL View
It supports SQL and SQLScript(**table function**). The latter is the same as the table function used in AMDP or ABAP CDS View.

### 2.2. Graphic View
It is similar to the HANA Calculation View. Graphic View is optimized and has better performance.

![alt text](/DataBuilder/images/NewGV.png?raw=true)

> [!IMPORTANT]
>-	It has "semantic type" as well. And, only the fact one can be used in the Analytic Model.
>-	The "attributes" are the same as "columns" defined in HANA view
>-  The attribute can have "association" too.
>-	It has "Input Parameter", as same as in HANA view. It should be pushed to lower node to get better performance and be mapped to the variable created in the upper layer like Analytic Model.
>-  Join, Union, Filter, Projection(show/hide columns), and Aggregation nodes are the same as in HANA Calculation View(Graphic).
>-  Data preview is available in each node.

#### 2.2.1. Association
Create a new GV using the previourly GV and add the associations

![alt text](/DataBuilder/images/NewGV_Asso.png?raw=true)

#### 2.2.2. Data Persistence
This is a feature that allows to load the snapshot of the view data into the memory to achieve the semi-realtime fuctionality and improve the query performance. It can be run onetime or by schculing jobs. 

![alt text](/DataBuilder/images/NewGV_Persistence.png?raw=true)

- Vuew Analyzer

- ![alt text](/DataBuilder/images/NewGV_Persistence.png?raw=true)

> Importnace
> This feature is similiar to PlanViz tool in HANA. It allows to analyze the SQL Execution Plan and understand the runtime and the reocrds selected in each node. In ddtionaion, it can teill how much memory the view may consume.



It is HANA PlanViz feature which allow we to analzye the exution plan of the view and the  ( number of records and the consumption of the memory)





## 3. ER Models
It provides a detailed view about how the model is designed.

![alt text](/DataBuilder/images/ERModel.png?raw=true)


## 4. Analytic Models

The Analytic Model must be built on the object of **Fact** semantic.

![alt text](/DataBuilder/images/AM.png?raw=true)

![alt text](/DataBuilder/images/NewAM.png?raw=true)

> [!Note]
>- We need to create the association in the fact table/view to bring in the attributes of the dimension.
>- We can create variables to map to the "input parameter" created in the graphic view.

**This is a good article about Analytic Model.**
- [Introducing the Analytic Model in SAP Datasphere](https://community.sap.com/t5/technology-blogs-by-sap/introducing-the-analytic-model-in-sap-datasphere/ba-p/13568591)

## 5. Currency Conversion Views
![alt text](/DataBuilder/images/Others.png?raw=true)

<pre>🚩 You can find the "HowTo" steps in the below link.</pre>
- [Howto](https://community.sap.com/t5/technology-blogs-by-members/currency-translation-in-sap-datasphere/ba-p/13688008)

## 6. Data Access Controls
<pre>🚩 This feature is not available in the trial version. You can find the detailed information in the below link.</pre>
- [Data Access Controls](https://community.sap.com/t5/technology-blogs-by-sap/sap-datasphere-security-amp-data-access-controls-overview/ba-p/13805353)

**The below link is the guide of the access control to the datasphere objects.**
- [Privileges and Permissions](https://help.sap.com/docs/SAP_DATASPHERE/9f804b8efa8043539289f42f372c4862/d7350c6823a14733a7a5727bad8371aa.html)
