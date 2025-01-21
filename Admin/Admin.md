# Administration

**First and foremost, I highly recommend this SAP Datasphere Expert [Content](https://help.sap.com/docs/SUPPORT_CONTENT/datasphere/4181116697.html). It's an outstanding resource packed with valuable information, clear concept explanations, and practical tips. Very Helpful!** 

## 1. Create Tenant
- **Tenant** is the environment within the SAP Business Technology Platform (BTP) where you can manage data and resources.
it is a common practice to create separate tenants for development (DEV), quality assurance (QAS), and production (PROD) environments in SAP Datasphere.

![alt text](/Admin/images/Space.png)


## 2. Create Space 
- **Space** a very important concept in SAP DataSphere. It is similar to the **workspace** in Azure Fabric/PowerBI. We can see the objects created in the current space and find the objects shared with you but created in the different spaces. 

> [!NOTE]
> Datasphere is a Data Mesh, using different **Spaces** for the data of different business branches. 
> 
> Even for IT, SAP recommends creating multiple spaces for dedicated functions. We may need to create a dedicated space for administration and a dedicated space to manage the virtual tables.
>
> Users can share the data(objects) to other **Spaces**.


## 3. SQL EndPoint (SQL Console or Database Explorer)
It is a very useful tool that provides the access to the underlying HANA Cloud. You can turn on the trace, analyze the execution plan, check the index server log and do all the troubleshooting at the HANA DB level.

<pre>🚩 Since this is a trial version, I have to omit this part as well. But you can find the details in the below link.</pre>
[Link](https://community.sap.com/t5/technology-blogs-by-members/sap-datasphere-how-to-integrate-open-sql-procedures-in-a-task-chain/ba-p/13860628) 

## 4. Connections

[Data Provisioning Agent(SDI)](https://community.sap.com/t5/technology-blogs-by-members/sap-datasphere-sap-data-provisioning-agent-upgrade/ba-p/13569884) and [SAP Cloud Connector](https://community.sap.com/t5/technology-blogs-by-sap/sap-datasphere-sap-cloud-connector-setup/ba-p/13550570) are needed in the setup of the connection from Datasphere to the on-premise systems.

You can check the status by clicking the **Validate** button or open the setting of the connection.
![alt text](/Admin/images/S4HC.png)

This is the connection to S/4HANA on-premise system.

> [!IMPORTANT]
> The **Replication Flow** and **Data Flow** are using SAP Cloud Connector.
>
> The **Remote Table** is using SDI(DP-Agent).
>
> This can be one of the factors that make you decide on using **Remote Table** or **Local Table** to build your models(**Views**).

What is SDI? Simply put, it is an ETL tool to access or load the data from external systems into HANA Database. It is like SAP Data Service(BODS), which is using the adapters, like ABAP, ODBC adpaters, to access to differnet source systems.

![alt text](/Admin/images/SDA.png)


## 5. Transport

<pre>🚩 Since this is a trial version, I have to omit this part as well. But you can find the details in the below blog</pre>
[blog](https://community.sap.com/t5/technology-blogs-by-members/life-cycle-management-in-sap-datasphere-transporting-content-between/ba-p/13576990)

## 6. Monitor

<pre>🚩 Since this is a trial version, I have to omit this part as well. But you can find the details in the below blog</pre>
[blog](https://community.sap.com/t5/technology-blogs-by-members/performance-monitoring-in-sap-datasphere/ba-p/13860769)

## 7. Manage User and Role

### 7.1 User Management
We can import the users from *CSV* file in the GoLive. And, we can synchronize the users and achieve the SSO via SAML. See this [Blog](https://community.sap.com/t5/technology-blogs-by-members/integrate-sap-data-warehouse-cloud-with-azure-active-directory/ba-p/13480455) for daily maintenance.

### 7.2 Role Management

This [link](https://community.sap.com/t5/technology-blogs-by-members/sap-datasphere-architecture-and-security-concept/ba-p/13702030) is about the architecture and security concept in Datashphere.

This is the [administration guide](https://help.sap.com/docs/SAP_DATASPHERE/9f804b8efa8043539289f42f372c4862/2d8b7d04dcae402f911d119437ce0a74.html).

**E.g.** You can find the role that contains the **update** privilege of the local tables. But it is an app feature. It does not say how to control the access to a specific object. 
![alt text](/Admin/images/Roles.png)

**SAP Best Practice - [link](https://community.sap.com/t5/technology-blogs-by-sap/sap-datasphere-security-amp-data-access-controls-overview/ba-p/13805353)**

## 8. Tools
The network connections are very critical as all the systems are now in Cloud environment. There are several measurement tools avaialble in SAC to run the test.

## 9. Cockpit
There seems to be no cockpit to have the statistics of the usage like the access number or the response time on the objects. 

Maybe we need to rely on the HANA views to get the information. See this [blog](https://community.sap.com/t5/technology-blogs-by-members/sap-datasphere-sap-hana-database-monitoring/ba-p/13696750).

Otherwise, we may leverage on the SAC cockpit. See the admin section in SAC.

