# Roadmap to SAP Datasphere

SAP is encouraging customers to transition to Datasphere. 


# 1. Migration

The path has been laid out to ensure a smooth migration and protect the investment in the BW system.

[Introducing the Migration from SAP BW to SAP Datasphere, SAP BW Bridge](https://learning.sap.com/learning-journeys/modernizing-your-data-warehouse-landscape-from-sap-bw-to-sap-datasphere/introducing-the-migration-from-sap-bw-to-sap-datasphere-sap-bw-bridge)

SAP recommends moving to BW Bridge first. It operates on SAP HANA Cloud platform but still includes the ABAP stack, enabling a seamless migration of BW objects.

![alt text](/Roadmap/images/Path.png?raw=true)


## 1.1. Migrate to BW Bridge

![alt text](/Roadmap/images/Bridge.png?raw=true)

- There are two ways to migrate the contents from on-promise BW system to BW Bridge.

  - Shell Conversion
Only the metadata of the objects are transferred. The data are reloaded from the source systems (S/4HANA or ERP).

  - Remote Conversion
Both the metadata and data are transferred. This is for the scenario where the historical data are not available in the source systems. After the conversion, the new data will be loaded from the source systems into BW Bridge.

- There are limitations of BW Bridger(See SAP Note 3117800). 
  - Queries are not supported.
  - No support for the OLAP engine and functionality dependent on the OLAP engine, e.g., analysis authorizations, query as InfoProvider, query execution, calculation of non-cumulative key figures (aka inventory key figures).
  - ....
  - 
The ADOs tables are replciated from BW bridge and the models are rebuilt in DataSphere. The new reports are created in SAC.
![alt text](/Roadmap/images/Future.png?raw=true)

## 1.2. Load data into DataSphere from the source systems(S/4HANA, ERP)

These are the Methods and Their Drawbacks

- BW SAPI Extractor
  - It may not be a long-term solution.
    
- CDSView Extractor (ODP)
  - Fewer customers develop the custom CDSView with the delta mechanism. 
  [Example](https://github.com/SAP-samples/teched2022-DA281/blob/main/exercises/dd1/README.md)

  - The doable way is to load the delta data from SAP standard CDSViews. 
  [HowTo](https://community.sap.com/t5/enterprise-resource-planning-blogs-by-sap/cds-based-data-extraction-part-ii-delta-handling/ba-p/13425761)

  - We need to rebuild the DataSphere **VIEWs** on top of these CDSViews structures. When we want to make enhancements, are we going to create the custom CDSView by referring to (copying) the SAP standard one?
  
- Tables (SLT)
  - Remodeling
    
# 2. Greenfield - BW SideCar + SLT

I think this approach is better and offers greater flexibility. The workload for remodeling is nearly the same as replicating CDSViews. SLT can replicate the delta data changes of the tables in real-time. We can compare the reports in datasphere side-by-side with the BW system.

[Link](https://learning.sap.com/learning-journeys/modernizing-your-data-warehouse-landscape-from-sap-bw-to-sap-datasphere/introducing-the-greenfield-approach)


# 3. User Management
We can import the users from *CSV* file in GoLive. And, we can synchronize the users and achieve the SSO via SAML. See [Blog](https://community.sap.com/t5/technology-blogs-by-members/integrate-sap-data-warehouse-cloud-with-azure-active-directory/ba-p/13480455)


# 4. Delta Loading
Generally this topic should be included in the Flow section in Databuilder. In fact, the Delta feature is quite simple and straight-forward within SAP DataSphere. We need to consider more when we integarate it with other system like S/4HANA and BW Brdige.

Let's take a quick at the **Delta** within Datasphere. We have talked about delta in the Flow and Model in DataBuilder section. We need to turn on "delta capture" in 
local table and use Trransfmoration Flow to do datla laoding.

# 4.1 In DataShphere 
# 4.1.1. Non-Delta Loaidng 
Souce Table - Non-Delta
Target Table - Detla
In such case, we can only choose "load type" to "Initial Only" in tranformation flow.

In the 1st exection, 3 records are loaded. We changed 1 record in the source table. In the TF log, we can see all 3 records are loaded again ito the target table.

# 4.1 Delta Loaidng 

Souce Table - Delta
Target Table - Detla



- You cannot choose "Initial and Detla" type in Transformation Flow if the source table does not support "Detla".
- You cannot use the Active Table of the source table which supports "Detla" mode and select "Initial and Delta" type in Transformation Flow. "initial Only" is the only option.
- You can choose "Initial Only" in the 1st execution in Transformation Flow and need to switch it back to "Initital and Delta" type in the consequtal exteion.. ( I am thinking why not selet "Initital and Delat" in the very beginning.

"Initial and Delta" only picks the changed records in the delta table of the source table after the last execution of Transformation Flow .

# 4.2 BW Bridge to DataSphere.

You can see the details in this [blog](https://community.sap.com/t5/technology-blogs-by-sap/delta-extraction-of-adso-from-sap-bw-bridge-into-sap-datasphere-via/ba-p/13651788) about how to load the delta records in ADSO changelog table in . Howerver, it does not have the case when \0RecordMode = 'A'. 

Using ADSOs still havery rely on the logics in the BW system. It is better to rebuild everything from the scrach.


