# Data Integration Monitor 

Manage, monitor and track the process of integrating data among the objects and systems.

## 1. Remote Tables
## 1.1. Full Data Replication

Snapshot data are loaded.
![alt text](/Integration/images/RD1.png?raw=true)

![alt text](/Integration/images/RD2.png?raw=true)

## 1.2. RealTime(Delta) Data Replication

It is only avaialbe for the datasource that supports CDC.

The initialization data are loaded. It took 70min to load 21M records.
![alt text](/Integration/images/RD3.png?raw=true)

It is active to replicate the delta data from remote table(CDS View) **IFIGLACCTLIR**.
![alt text](/Integration/images/RD4.png?raw=true)

- Details - [SAP Help](https://help.sap.com/docs/SAP_DATASPHERE/be5967d099974c69b77f4549425ca4c0/441d327ead5c49d580d8600301735c83.html)
  - No logs are generated when data is replicated in real-time mode. The displayed logs relate to previous actions.
  - Remote object needs to be a table of type "COLUMN TABLE" (other table types like Row Tables or Virtual Tables not supported)

> [!Note]
> For the Realtime Data Replication(Delta Data Loading), these CDSViews are leveraging on ODP. So they need to have @Analytics.dataExtraction.enabled + CDC(delta.changeDataCapture). And,
> it does not support the CDSViews with **Generic Date/Timestamp Delta** which is using the **"PULL"** mode. We still need to use **"Replication Flow"** to do the delta data loading.
>
> You can find the details in the **Flow** of **DataBuilder** section or in [Datasphere Expert Content](https://help.sap.com/docs/SUPPORT_CONTENT/datasphere/4723641935.html)

## 2. Views

Monitor the jobs of loading the **View** persistence data into memory

![alt text](/Integration/images/DIM_View.png?raw=true)

## 3. Flows

Montoir the jobs of the data **Flows**

![alt text](/Integration/images/Flows_log.png?raw=true)

### 3.1. Log of Data Flow

![alt text](/Integration/images/DF_log.png?raw=true)

Method **insert** is used in Data Flow.

![alt text](/Integration/images/INSERT.png?raw=true)

### 3.2. Log of Transfomration Flow

![alt text](/Integration/images/TF_log.png?raw=true)

Method **upsert** is used in Transformation Flow.

![alt text](/Integration/images/UPSERT.png?raw=true)

