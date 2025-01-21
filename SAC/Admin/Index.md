# Administration

# 1. Create Tenant and Spaces

As in **Datasphere**, we need to create the tenant and the workspaces for different business branches. [Blog](https://community.sap.com/t5/technology-blogs-by-members/sap-analytics-cloud-workspaces/ba-p/13531009)

If it is in the same tenatn with **Datasphere**, we can switch between **SAC** and **Datasphere** easily.

![alt text](/SAC/Admin/images/SAC_DS.png)

# 2. Connections

## 2.1. On-Premise System

### 2.1.1. Live Connetion

There is no data loaded into the SAC. The web browse will receive the metadata from the SAC and the data from the on-premeise system. Browsers follow a same-original policy. It forbids web-plages from sending requests to other websites or servers that are not trusted. Thus we need set up **CORS** or **Tunner** to make the trust relationship.

See the details in [SAP help](https://help.sap.com/docs/SAP_ANALYTICS_CLOUD/00f68c2e08b941f081002fd3691d86a7/c1cbf644b0a1434fbb4ea072a0562286.html)

SAC consumes the queries in S/4HANA or BW systems via the OLAP connection.

### 2.1.2. Import Connetion

Please find the details in this [blog](https://community.sap.com/t5/technology-blogs-by-members/import-data-connection-to-sap-s-4hana-in-sap-analytics-cloud-technical/ba-p/13697364).

The data of CDSView queries(embedded analytics) are loaded into **SAC** via the **OData** service in S/4HANA.

OData is used to import the data from **Datasphere** into SAC as well. See this [article](https://www.seaparkconsultancy.com/single-post/uniting-sap-datasphere-with-sap-analytics-cloud-for-data-harmony-revolutionize-your-data-strategy-2).  

## 2.2. Cloud system

![alt text](/SAC/Admin/images/CC.png)
We can create the LiveConnection to the Datasphere system. In addtion, the LiveConnection is also used by the SAP Analytics Cloud Add-In.

# 3. Users/Permissions

-  Do NOT use the default roles
-  Use Teams to group your Roles (Team in SAC = Group in BOBJ = Composite Role in S/4)
-  ....
   
This is SAP [best practice](https://help.sap.com/docs/SUPPORT_CONTENT/boc/3354605643.html).

> [!NOTE]
> SAP BOBJ can seamless integrate the security of S/4HANA or BW. It can import the role defined in ABAP system.
>
> However, I cannot find how to achieve that in Datasphere and SAC. 


# 4. Transport
In theory, we need to set up three DEV, QAS and PROD environments.

Due to the trial system, I don't the access to the CI/DI function.

# 5. Cockpit
The statistics are very important for the dialy monitoring and maintenance of the system. But, as I am on the trial version, I am not able to dive into this function. See details [here]([# 4. Transport](https://community.sap.com/t5/technology-blogs-by-sap/sap-analytics-cloud-administration-cockpit/ba-p/13515678)

# 6. Tools
The network connections are very critical as all the systems are now in Cloud environment. There are several measurement tools avaialble in SAC to run the test.

![alt text](/SAC/Admin/images/TOOLS1.png)

> [!NOTE]
> Your browser and hardware performance will be scored based on multiple measurements.
> 
> Score >= 75: Excellent
> 
> Score >= 50 and < 75: Good
> 
> Score < 50: Poor



