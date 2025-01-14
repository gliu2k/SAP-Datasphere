# Data Builder - Model

In fact, it contains not only the model components but also the ETL elements. In this section, I will focus on the data modeling part.

![alt text](/DataBuilder/images/DataBuilder.png?raw=true)


# 1. Tables

You can create a local table, generate a **local** table by importing CSV file, or import remote tables or CSN/JSON file which is for all objects like View or Analytic Model.

![alt text](/DataBuilder/images/Tables.png?raw=true)

## 1.1. Import Remote Tables (from S/4HANA)

## 1.1.1. Import CDS Views from on-premise S/4HANA

**Data Provisioning Agent(SDI)** must be installed and configured(ABAP Adapter).
![alt text](/DataBuilder/images/Import1.png?raw=true)
All the CDSViews(SQLViews) are in the list. 
![alt text](/DataBuilder/images/Import2.png?raw=true)
![alt text](/DataBuilder/images/Import3.png?raw=true)
The selected CDSView is imported and delployed. Its type is "Remote Table".
![alt text](/DataBuilder/images/Import4.png?raw=true)
The data, which have not yet been replciated, can be displayed via SDA.
![alt text](/DataBuilder/images/Import5.png?raw=true)

> [!NOTE]
> Remote tables are the virtual as in SDA(HANA) or the “link” as in Azure Fabric, which map to the physical objects locating in the remote system. 
> The object and its data are stored in the remote system, which is on-premise S/4HANA in this case. It also means that you can get the real-time data. However, the performance can be slow if the source system is on-premise and target system is on-cloud. (It is slow even when both systems are on-premise in SDA).
>
> You can replicate all the data into the snapshot or do realtime replication if the datasource is supported(See section **Integration**).

- **Remote Table vs Local Table (Using Replication Flow)**
  
> [!NOTE]
> The details can be found in [SAP Help](https://help.sap.com/docs/SUPPORT_CONTENT/datasphere/4723641935.html)

> [!IMPORTANT]
> **All** the CDSViews(and ABAP tables/views) in S/4HANA can be used(mapped) as the remote tables in Datasphere. They don't have to have the **Analytics.dataExtraction.enabled+Delta** setting except for the realtime replication. And when you get an enhancement requirement, it is easier to expose the new added fields in the CDSViews and don't need to add these fields into the local table as well.

## 1.2. Import Entities (from BW)

It is possible to import the objects in BW system as the remote tables(virtual objects) in Datasphere.

![alt text](/DataBuilder/images/RemoteEntity.png?raw=true)

## 1.3. Create a new local Table (Datashpere) 

### 1.3.1. Table Partition

If you have a good understanding of the table's size and expected data growth, it's advisable to decide on partitioning when you create the table from the performance perspective.

![alt text](/DataBuilder/images/Partition.png?raw=true)

### 1.3.2. Semantic Usage
![alt text](/DataBuilder/images/NewTable.png?raw=true)

> [!IMPORTANT] 
> -	**Fact**: Transaction Data and the only type can be used in creating Analytic Model
> -	**Dimension/Text/Hierarchy**: master data and are used in the association of fact, view or other dimension tables 

### 1.3.3. Association
Add the attributes/text to the field. The association will be availabe in creating the Analytic Model.

![alt text](/DataBuilder/images/TableAssociation.png?raw=true)


### 1.3.4. Delta Capture 

![alt text](/DataBuilder/images/TableDelta.png?raw=true)

> [!IMPORTANT] 
> - Two local tables, the active table and the detla table("Technicalname_Delta"), are generated when the “Delat Capture” flag is turned on. 
> - Two additional fields, "Change Type" and "Change Datae" are included in the "delta" table. The "Change Type" can have value of "I"(initial), "D"(delete) and "U"(update) after specific activities are applied to the record.

It will be explained in details again in the **Roadmap** section.

# 2. Views

There are two types of views, SQL View and Graphical View, in datasphere. Both are virtual objects. <BR/>

![alt text](/DataBuilder/images/Views.png?raw=true)

## 2.1. SQL View
It supports SQL and SQLScript(**table function**). The latter is the same as the table function used in AMDP or ABAP CDS View.

## 2.2. Graphical View

You can directly select the table from the source system and deploy it as the remote table, and then use it as the data source of the view.

![alt text](/DataBuilder/images/RT.png?raw=true)

It is similar to the HANA Calculation View. Graphical View is optimized and has better performance.

![alt text](/DataBuilder/images/NewGV.png?raw=true)

> [!IMPORTANT]
>-	View has "semantic type" as well. And, only the fact view can be used in the Analytic Model.
>-	The "attributes" are the same as "columns" defined in HANA view
>-  The attribute can have "association". Please note that there is no **"Star Join"** type because this feature is the same as the "Star Join".
>-	It has "Input Parameter" which is the same as in HANA view. It should be pushed down to the lower node to get better performance and be mapped to the variable created in the upper layer like Analytic Model.
>-  **Join, Union, Filter, Projection(show/hide columns), and Aggregation nodes** are the same as in HANA Calculation View(Graphical).
>-  **Data preview** is available in each node.

> [!Tip]
> **Performance tuning**
> - Set the correct join cardinalities for JOIN prune
> - There is no UNION prune as in SAP HANA Views

### 2.2.1. Association
Create a new GV using the previously GV and add the associations (as in the local table). It can be used in creating Aanlytic Model.

![alt text](/DataBuilder/images/NewGV_Asso.png?raw=true)

### 2.2.2. Data Persistence
This is a feature that allows to load the snapshot of the view data into the memory to achieve the semi-realtime functionality and improve the query performance. It can be run once or scheduled to run as a recurring job.

![alt text](/DataBuilder/images/GV_Persistence.png?raw=true)

### 2.2.3. View Analyzer

> [!IMPORTANT] 
> This feature is similar to the **PlanViz** tool in HANA. It allows for the analysis of the SQL Execution Plan, providing insights into query runtime and memory consumption.

![alt text](/DataBuilder/images/GV_Analyzer1.png?raw=true)

![alt text](/DataBuilder/images/GV_Analyzer2.png?raw=true)

![alt text](/DataBuilder/images/GV_Analyzer3.png?raw=true)

- In the above analysis result, which is available in "Data Integration Monitor", we can find the following important execution information. 

  -  Run Time
  -  Memory Consumption
  -  Statistics (processed records in each node)

### 2.2.4. Linage Analysis

"Linage Analysis" is kind like the combination of "displaying the dependencies" in CDSView and "showing the where-used" list in SAP.

![alt text](/DataBuilder/images/LinageAnalysis.png?raw=true)

> [!Note] 
>  **Don't forget to unfold the '+' on the very right of the last object.** to show the relevant upper objects

![alt text](/DataBuilder/images/WhereUsed.png?raw=true)


### 2.2.5. Data Access Controls

Apply the access to the view data at the row-level. 
It is very similarly to the **Analytic Privileges** in SAP HANA and is defined in **Piont 6** of this section.

![alt text](/DataBuilder/images/GV_DCA.png?raw=true)

# 3. ER Models
It provides a detailed view about how the model is designed. I don't think it has extensive usage in the real business scenarios. 

![alt text](/DataBuilder/images/ERModel.png?raw=true)


# 4. Analytic Models

The Analytic Model must be built on the object of **Fact** semantic.

![alt text](/DataBuilder/images/AM.png?raw=true)

![alt text](/DataBuilder/images/NewAM.png?raw=true)

> [!Note]
>- We need to create the association in the fact table/view and bring in the association, the attributes of the dimension, here. In other words, you cannot create JOIN/UNION/Association in Analytic Model.
>- We can create variables to map to the "input parameter" created in the graphic view.

**This is a good article regarding Analytic Model.**
- [Introducing the Analytic Model in SAP Datasphere](https://community.sap.com/t5/technology-blogs-by-sap/introducing-the-analytic-model-in-sap-datasphere/ba-p/13568591)

# 5. Currency Conversion Views
![alt text](/DataBuilder/images/Others.png?raw=true)

<pre>🚩 You can find the "HowTo" in the below link.</pre>
- [Howto](https://community.sap.com/t5/technology-blogs-by-members/currency-translation-in-sap-datasphere/ba-p/13688008)

# 6. Data Access Controls

There are 3 types of DAC. 
- Single value DAC
- Operator and values DAC
- Hierarchy DAC

**How to create a single value DAC:**
1. Create a new **local table** with a field as the filter(control on the values) of the same field in **View**

2. Create a Data Access Control(DAC) and define the DAC artifact by using the lcoal time above

3. Add the DAC into **View**

The details can be found in this [blog](https://community.sap.com/t5/technology-blogs-by-members/data-access-control-in-sap-datasphere-single-value-dac/ba-p/13705980)
  
**This is SAP Best Practice of [DAC](https://community.sap.com/t5/technology-blogs-by-sap/sap-datasphere-security-amp-data-access-controls-overview/ba-p/13805353)**

------------------------------------------------------------------------------------------------------------------------------------
Datasphere is a Data Mesh, using differnt **Spaces** for different business branches.

**The below link is about the architecture and security concept in Datashphere.** 
- [Concept](https://community.sap.com/t5/technology-blogs-by-members/sap-datasphere-architecture-and-security-concept/ba-p/13702030)


**The below link is the guide of the access control to the datasphere objects.**
- [Privileges and Permissions](https://help.sap.com/docs/SAP_DATASPHERE/9f804b8efa8043539289f42f372c4862/d7350c6823a14733a7a5727bad8371aa.html)


