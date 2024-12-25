#  Data Builder - Flows

![alt text](/DataBuilder/images/Flows.png?raw=true)

# 1. Replication Flow 

- Copy the data from one or multiple (remote) source systems into datasphere(local) at. There is no transformation.

It is used to copy the data first in a limited time window.

![alt text](/DataBuilder/images/R_Flow.png?raw=true)

# 2. Data Flow 

- Load and transform (Join, Union and python scritp) the data from the source to the target. It does not support delta (**insert** method). We must truncate the target table before reloading the data.

![alt text](/DataBuilder/images/DF_Flow.png?raw=true)


# 3. Transformation Flow 

It is an ETL and is similiar to BW transformation but is using the HANA view features to convert the data.

![alt text](/DataBuilder/images/TF_Flow.png?raw=true)

> [!IMPORTANT] 
> - Support delta loading (**ONLY** load the changed data in the source table. We have covered it in the databuilder section)  
> - Easy for trouble-shooting if the source ocntans bad data
> - Use **upsert** method, which means we don't need to clear the target table

#3.1 SQLCript View(Table Function)

#3.2 Graphics View

![alt text](/DataBuilder/images/TF_Flow.png?raw=true)
>  [!TIP]
> You can leverage an existed view, graphics or SQL, in the transformation flow.

# 4. Intelligent Lookups

This is a new feature. It is similar to **Fuzzy** join in Azure Fabric. You can find the datails in the below link.
[Blog]( https://community.sap.com/t5/technology-blogs-by-sap/sap-datasphere-intelligent-lookup-series-what-is-a-fuzzy-match-and-why/ba-p/13558732)
