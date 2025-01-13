#  Data Builder - Flows

![alt text](/DataBuilder/images/Flows.png?raw=true)

# 1. Replication Flow 

Copy the data from one or multiple source systems into datasphere(local). There is no transformation.

> [!IMPORTANT] 
>🚩  **It can be used to load the data from source BW or S/4HANA systems and reversly.**
> 
> Here is an excellent [series](https://community.sap.com/t5/technology-blogs-by-sap/replication-flow-blog-series-part-1-overview/ba-p/13581472) on Replication Flow and also this [blog](https://community.sap.com/t5/technology-blogs-by-members/sap-datasphere-replication-flow-delta-functionality/ba-p/13927903).
>
> It supports ODP(DataSource - CDSViews/SAPI) and SLT(Table/CDSViews). Find more information in **Roadmap* section.

**Below** is the scenario of loading the data from a SAP standard CDS View with **Analytics.dataExtraction.enabled + Delta** of the on-premise S/4HANA system into the local table imported from Datasphere Business Content.

**Source SAP Standard CDS View:** C_SalesDocumentItemDEX_1 (dataCategory: #FACT). It is used as a sample to explain delta capture in **Roadmap** section.

```
@AbapCatalog.sqlViewName: 'CSDSLSDOCITMDX1'
@AbapCatalog.compiler.compareFilter: true
@AbapCatalog.preserveKey: true
@AccessControl:{
    authorizationCheck: #CHECK,
    personalData.blocking: #('TRANSACTIONAL_DATA')
}
@EndUserText.label: 'Data Extraction for Sales Document Item'
@ClientHandling.algorithm: #SESSION_VARIABLE
@ObjectModel.usageType.dataClass: #TRANSACTIONAL
@ObjectModel.usageType.serviceQuality: #D
@ObjectModel.usageType.sizeCategory: #XL
@ObjectModel.representativeKey: 'SalesDocumentItem'
@VDM.viewType: #CONSUMPTION
@Metadata.ignorePropagatedAnnotations: true
@ObjectModel.modelingPattern: #NONE
@ObjectModel.supportedCapabilities:  [ #EXTRACTION_DATA_SOURCE ]

@Analytics: {
    dataCategory: #FACT,
    dataExtraction: {
        enabled: true,
        delta.changeDataCapture: {
            mapping:[
                {
                    table: 'vbap', role: #MAIN,
                    viewElement: ['SalesDocument', 'SalesDocumentItem'],
                    tableElement: ['vbeln', 'posnr']
                },
                {
                    table: 'vbak', role: #LEFT_OUTER_TO_ONE_JOIN,
                    viewElement: ['SalesDocument'],
                    tableElement: ['vbeln']}
            ]
        }
    }
 }

define view C_SalesDocumentItemDEX_1
as select from I_SalesDocumentItem as SalesDocumentItem
left outer to one join I_SalesDocument              as SalesDocument          on SalesDocumentItem.SalesDocument = SalesDocument.SalesDocument
left outer to one join I_CompanyCode                as CompanyCode            on  SalesDocument.BillingCompanyCode = CompanyCode.CompanyCode
//Extensibility
association [0..1] to E_SalesDocumentItemBasic      as _ExtensionItem         on  $projection.SalesDocument     = _ExtensionItem.SalesDocument
                                                                              and $projection.SalesDocumentItem = _ExtensionItem.SalesDocumentItem
association [0..1] to E_SalesDocumentBasic          as  _ExtensionHeader      on  $projection.SalesDocument     = _ExtensionHeader.SalesDocument
{
    // Key
    @ObjectModel.foreignKey.association: '_SalesDocument'
    key SalesDocumentItem.SalesDocument,
    key SalesDocumentItem.SalesDocumentItem,
```
    
**Target local Table:** SAP_SD_IL_C_SALESDOCUMENTITEMDEX_1 (Its "Delta Capture" is ON)

Select Source Connection - S/4HANA (ABAP)
![alt text](/DataBuilder/images/RF1.png?raw=true)
Select Source Container - CDS_Extraction(ODP)
![alt text](/DataBuilder/images/RF2.png?raw=true)
Add Source Object
![alt text](/DataBuilder/images/RF3.png?raw=true)
Select CDS View
![alt text](/DataBuilder/images/RF4.png?raw=true)
Select Target Connection - Datasphere (Local Repository)
![alt text](/DataBuilder/images/RF5.png?raw=true)
Select Target - Local Table
![alt text](/DataBuilder/images/RF6.png?raw=true)
Map to existing Target Object
![alt text](/DataBuilder/images/RF7.png?raw=true)
Set load type (Iniital and Delta) 
![alt text](/DataBuilder/images/RF8.png?raw=true)
Set the frequency to 1 time per hour for the dalta data loading
![alt text](/DataBuilder/images/RF9.png?raw=true)
Save and Deploy the Replication Flow 
![alt text](/DataBuilder/images/Deploy_Error.png?raw=true)
> [!Note] 
> I got an error in deploying the Replication Flow due to the different types defined for the same field included in the source and target systems. So, I made the change in the target table as we used to do BW development. In BW implmentation, we usually copy the BI Content and make the enhancement to the copied Z-object.
>

# 2. Data Flow 

Load and transform (Join, Union, Projection, Aggregation and **Python** script) the data from the source to the target. As it does not support delta (it uses the **insert** method), we must truncate the target table before reloading the data.

![alt text](/DataBuilder/images/DF_CDS.png?raw=true)

> [!IMPORTANT]
> It supports ODP(DataSource - CDSViews/SAPI) and SLT(Table/CDSViews). In the above, the CDSViews Extractors as the datasources in the on-premise S/4HANA system are **Analytics.dataExtraction.enabled**.
> 
> It does not support delta data loading.
>
> It can be used to load the data within Datasphere.


![alt text](/DataBuilder/images/Flow_DF.png?raw=true)

> [!CAUTION]
> The above DF job failed because I did not truncate the target table before reloading the data. The deteails are explained in the **Data Integration Monitor** section.
 
# 3. Transformation Flow 

It is an ETL process similar to BW transformation, but it uses **VIEW** to transform the data.

It is the only **flow** that is used within DataSphere.

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


