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
