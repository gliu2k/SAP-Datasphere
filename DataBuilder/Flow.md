#  Data Builder - Flows

![alt text](/DataBuilder/images/Flows.png?raw=true)

# 1. Replication Flow 

Copy the data from one or multiple (remote) source systems into datasphere(local) at. There is no transformation.

It is used to copy the data first in a limited time window.

**Here is a link to an excellent series on Replication Flow.** [Blog](https://community.sap.com/t5/technology-blogs-by-sap/replication-flow-blog-series-part-1-overview/ba-p/13581472)


# 2. Data Flow 

Load and transform (Join, Union, Projection, Aggregation and **Python** script) the data from the source to the target. It does not support delta (**insert** method). We must truncate the target table before reloading the data.

![alt text](/DataBuilder/images/Flow_DF.png?raw=true)

> [!CAUTION]
> The above DF job failed because I did not truncate the target table before reloading the data. The deteails are explained in the **Data Integration Monitor** section.

# 3. Transformation Flow 

It is an ETL and is similiar to BW transformation but is using the **VIEW** features to convert the data.

![alt text](/DataBuilder/images/Flow_TF1.png?raw=true)

> [!IMPORTANT] 
> - Support delta loading (**ONLY** load the changed data in the source table. We have covered it in the databuilder section)  
> - Easy for trouble-shooting if the source ocntans bad data
> - Use **upsert** method, which means we don't need to clear the target table

# 3.1. SQLCript View(Table Function)

![alt text](/DataBuilder/images/Flow_TF2.png?raw=true)

# 3.2. Graphical View

![alt text](/DataBuilder/images/Flow_GV1.png?raw=true)
>  [!TIP]
> You can leverage an existed view, Graphical or SQL view, in the transformation flow as in the below screenshot.

![alt text](/DataBuilder/images/Flow_GV2.png?raw=true)

# 4. Intelligent Lookups

This is a new feature. It is similar to **Fuzzy** join in Azure Fabric. You can find the datails in the below link.

[Blog]( https://community.sap.com/t5/technology-blogs-by-sap/sap-datasphere-intelligent-lookup-series-what-is-a-fuzzy-match-and-why/ba-p/13558732)
