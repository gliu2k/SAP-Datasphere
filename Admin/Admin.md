# Administration

**First and foremost, I highly recommend this SAP Datasphere Expert [Content](https://help.sap.com/docs/SUPPORT_CONTENT/datasphere/4181116697.html). It's an outstanding resource packed with valuable information, clear concept explanations, and practical tips. Very Helpful!** 

## 1. Create Tenant
- **Tenant** is the environment within the SAP Business Technology Platform (BTP) where you can manage data and resources.
it is a common practice to create separate tenants for development (DEV), quality assurance (QAS), and production (PROD) environments in SAP Datasphere.

![alt text](/Admin/images/Space.png)

<pre>🚩 Since this is a trial version, I will omit the details of transport.</pre>

## 2. Create Space 
- **Space** a very important concept in SAP DataSphere. It is similar to the **workspace** in Azure Fabric/PowerBI. We can see the objects created in the current space and find the objects shared with you but created in the different spaces. 

> [!NOTE]
> SAP recommends creating multiple spaces for dedicated functions. We may need to create a dedicated space for administration. It it better to create a dedicated space to manage the virtual tables.


## 3. SQL EndPoint (SQL Console or Database Explorer)
It is a very useful tool that provides the access to the underlying HANA Cloud. You can turn on the trace, analyze the execution plan, check the index server log and do all the troubleshooting at the HANA DB level.

<pre>🚩 Since this is a trial version, I have to omit this part as well. But you can find the details in the below link.</pre>
[Link](https://community.sap.com/t5/technology-blogs-by-members/sap-datasphere-how-to-integrate-open-sql-procedures-in-a-task-chain/ba-p/13860628) 

## 4. Connections

[Data Provisioning Agent(SDI)](https://community.sap.com/t5/technology-blogs-by-members/sap-datasphere-sap-data-provisioning-agent-upgrade/ba-p/13569884) and [SAP Cloud Connector](https://community.sap.com/t5/technology-blogs-by-sap/sap-datasphere-sap-cloud-connector-setup/ba-p/13550570) are needed in the setup of the connection from Datasphere to the on-premise systems.

You can check the status by clicking the **Validate** button or open the setting.
![alt text](/Admin/images/S4HC.png)

This is the connection to S/4HANA on-premise system.

> [!IMPORTANT]
> The **Replication Flow** and **Data Flow** are using SAP Cloud Connector.
>
> The **Remote Table** is using SDI(DP-Agent).
>
> This can be one of the factors make you decide on using **Remote Table** or **Local Table** to build your models(VIEWs).

What is SDI? Simply put, it is an ETL tool to access or load the data from external systems into HANA Database. It is like SAP Data Service(BODS), which is using the adapters, like ABAP, ODBC adpaters, to access to differnet source systems.

![alt text](/Admin/images/SDA.png)


## 5. Transport
It is not avaible in the trial version. You can find many resources by searching Google. This is a good [blog](https://community.sap.com/t5/technology-blogs-by-members/life-cycle-management-in-sap-datasphere-transporting-content-between/ba-p/13576990)

## 6. Monitor
It is not avaible in the trial version. You can find many resources by searching Google. This is a good [blog](https://community.sap.com/t5/technology-blogs-by-members/performance-monitoring-in-sap-datasphere/ba-p/13860769)

## 7. User Management
We can import the users from *CSV* file in the GoLive. And, we can synchronize the users and achieve the SSO via SAML. See [Blog](https://community.sap.com/t5/technology-blogs-by-members/integrate-sap-data-warehouse-cloud-with-azure-active-directory/ba-p/13480455) in daily maintenance.

**There is a [blog](https://community.sap.com/t5/technology-blogs-by-sap/integrate-sap-s-4hana-authorizations-into-sap-datasphere/ba-p/13644117 ) about how to integrate the authoriztions defined in S/4HANA system into Datasphere. If we can synchronize the tables of SAP roles and users in S/4HANA, we won't need to assign some roles to the users manually in Datasphere. SAP GRC system can automate the process.**

