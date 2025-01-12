# Administration

## 1. Create Tenant
- **Tenant** is the environment within the SAP Business Technology Platform (BTP) where you can manage data and resources.
it is a common practice to create separate tenants for development (DEV), quality assurance (QAS), and production (PROD) environments in SAP Datasphere.

![alt text](/Admin/images/Space.png)

<pre>🚩 Since this is a trial version, I will omit the details of transport.</pre>

## 2. Create Space 
- **Space** a very important concept in SAP DataSphere. It is similar to the **workspace** in Azure Fabric/PowerBI. We can see the objects created in the current space and find the objects shared with you but created in the different spaces. 

> [!NOTE]
> SAP recommends creating multiple spaces for dedicated functions. We may need to create a dedicated space for administration. It it better to create a dedicated space to manage the virtual tables.


## 3. SQL EndPoint
It is a very useful tool that provides access to the underlying HANA Cloud.

See [details](https://community.sap.com/t5/technology-blogs-by-members/sap-datasphere-how-to-integrate-open-sql-procedures-in-a-task-chain/ba-p/13860628)

## 4. Connections

[Data Provisioning Agent(SDI)](https://community.sap.com/t5/technology-blogs-by-members/sap-datasphere-sap-data-provisioning-agent-upgrade/ba-p/13569884) and [SAP Cloud Connector](https://community.sap.com/t5/technology-blogs-by-sap/sap-datasphere-sap-cloud-connector-setup/ba-p/13550570) are needed in the setup of the connection from Datasphere to the on-premise systems.

> [!IMPORTANT]
> The **Replication Flow** is using SAP Cloud Connector and the **Remote Table** needs SDI/RDA. This can be one of the factors make you decide on using **Remote Table** or **Local Table** to build your models(VIEWs).

What is SDI? Simply put, it is an ETL tool to load data from external systems into HANA Database. Just like SAP Data Service(BODS), it has the adapters, like ABAP, ODBC to access to differnet source systems.

![alt text](/Admin/images/SDA.png)

The Cloud Connector establishes a secure connection between the cloud and on-premise systems. See this [course](
https://learning.sap.com/learning-journeys/connecting-sap-btp-and-on-premise-systems-using-the-cloud-connector/defining-the-cloud-connector_c7fa42b9-0cb1-46ae-aede-f30bc13e94ae) 

-BW Bridge
In this [article](https://community.sap.com/t5/technology-blogs-by-members/sap-datasphere-sap-bw-bridge-and-cloud-connector-configuration/ba-p/13580094), it explains the details about how to connect Datasphere, BW modeling tool, on-promise system to BW Bridge system.

## 5. Transport
It is not avaible in the trial version. You can find many resources by searching Google. This is a good [blog](https://community.sap.com/t5/technology-blogs-by-members/life-cycle-management-in-sap-datasphere-transporting-content-between/ba-p/13576990)

## 6. Monitor
It is not avaible in the trial version. You can find many resources by searching Google. This is a good [blog](https://community.sap.com/t5/technology-blogs-by-members/performance-monitoring-in-sap-datasphere/ba-p/13860769)

