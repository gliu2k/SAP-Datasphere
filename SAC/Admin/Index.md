# Administration

# 1. Create Tenant and Spaces

As in **Datasphere**, we need to create the tenant and the workspaces for different business branches. [Blog](https://community.sap.com/t5/technology-blogs-by-members/sap-analytics-cloud-workspaces/ba-p/13531009)

If it is in the same tenatn with **Datasphere**, we can switch **SAC** and **Datasphere** easily.


# 2. Connections

## 2.1. On-Premise System

### 2.1.1. Live Connetion

There is no data load into the SAC. The web browse will receive the metadata from the SAC and the data from the on-premeise system. Browsers follow a same-original policy. It forbids web-plages from sending requests to other websites or servers that are not trusted. Thus we need set up **CORS** or **Tunner** to make the trust relationship.

See the details in [SAP help](https://help.sap.com/docs/SAP_ANALYTICS_CLOUD/00f68c2e08b941f081002fd3691d86a7/c1cbf644b0a1434fbb4ea072a0562286.html)

SAC consumes the queries in S/4HANA or BW systems via the OLAP connection.

### 2.1.2. Import Connetion

Please find the details in this [blog](https://community.sap.com/t5/technology-blogs-by-members/import-data-connection-to-sap-s-4hana-in-sap-analytics-cloud-technical/ba-p/13697364).

The data of CDSView queries(embedded analytics) are loaded into **SAC** via the **OData** service in S/4HANA.

OData is used to import the data from **Datasphere** into SAC as well. See this [article](https://www.seaparkconsultancy.com/single-post/uniting-sap-datasphere-with-sap-analytics-cloud-for-data-harmony-revolutionize-your-data-strategy-2).  

## 2.2. Cloud system

![alt text](/SAC/Admin/images/CC.png)
We can create the LiveConnection to the Datasphere system. In addtion, the LiveConnection is also used by the SAP Analytics Cloud Add-In.

## 3. Users/Permissions
To be added...

## 4. Transport
In theory, we need to set up three DEV, QAS and PROD environments.
