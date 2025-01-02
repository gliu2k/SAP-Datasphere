#  Data Builder - Flows

![alt text](/DataBuilder/images/Flows.png?raw=true)

# 1. Replication Flow 

Copy the data from one or multiple (remote) source systems into datasphere(local). There is no transformation.

It is used to copy the data first in a limited time window.

Here is an excellent [series](https://community.sap.com/t5/technology-blogs-by-sap/replication-flow-blog-series-part-1-overview/ba-p/13581472) on Replication Flow.


> [!IMPORTANT] 
>🚩  **It can be used to load the delta data from source BW or S/4HANA systems.**
>
> Based on the 'Source Connection' type **Delta** option will be enabled in Replication Flow. See [blog](https://community.sap.com/t5/technology-blogs-by-members/sap-datasphere-replication-flow-delta-functionality/ba-p/13927903).
>
> Either ODP or SLT needs to be configured to enable delta capture. See the [details](https://github.com/SAP-samples/teched2022-DA281/blob/main/exercises/dd3/README.md).



# 2. Data Flow 

Load and transform (Join, Union, Projection, Aggregation and **Python** script) the data from the source to the target. As it does not support delta (it uses the **insert** method), we must truncate the target table before reloading the data.

![alt text](/DataBuilder/images/Flow_DF.png?raw=true)

> [!CAUTION]
> The above DF job failed because I did not truncate the target table before reloading the data. The deteails are explained in the **Data Integration Monitor** section.

# 3. Transformation Flow 

It is an ETL process similar to BW transformation, but it uses **VIEW** to transform the data.

![alt text](/DataBuilder/images/Flow_TF1.png?raw=true)

> [!IMPORTANT] 
> - Support **delta** loading (**ONLY** load the changed data in the detla table of the source. It is also covered in the **Databuilder/Model** and **Roadmap** sections.)  
> - Easy for troubleshooting if the source contains bad data
> - Use **upsert** method, which means we don't need to clear(truncate) the target table first

## 3.1. SQLScript View(Table Function)

![alt text](/DataBuilder/images/Flow_TF2.png?raw=true)

## 3.2. Graphical View

![alt text](/DataBuilder/images/Flow_GV1.png?raw=true)
>  [!TIP]
> You can leverage an existing view, Graphical or SQL view, in the transformation flow as shown in the below screenshot.

![alt text](/DataBuilder/images/Flow_GV2.png?raw=true)

# 4. Task Chains

It is similar to BW Process Chain. 

![alt text](/DataBuilder/images/Flow_TaskChains.png?raw=true)

# 5. Intelligent Lookups

This feature is like **Fuzzy** join in **Azure Fabric**. You can find the details about it in this [blog]( https://community.sap.com/t5/technology-blogs-by-sap/sap-datasphere-intelligent-lookup-series-what-is-a-fuzzy-match-and-why/ba-p/13558732).

![alt text](/DataBuilder/images/Flow_InetLookups.png?raw=true)


