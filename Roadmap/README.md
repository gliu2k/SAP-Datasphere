# Roadmap to SAP Datashpere

SAP is persuading the customers to move to Datasphere. The way has been paved to make sure the smooth migration and guarantee the investment in BW system. 

SAP suggests moving to BW Bridger, a persist layer in SAP cloud. It is on HANA Cloud platform but still has ABAP stack, which makes it possible to migrate the BW objects smoothly.  

![alt text](/Roadmap/images/Path.png?raw=true)

## 1. Migratie to BW Bridge

![alt text](/Roadmap/images/Bridge.png?raw=true)
There are two ways to migrate the contents from on-promise BW system to BW Bridge.

- Script
Only the metadata of the objects are converted. The data are reloaded from the source systems (S/4HANA or ERP).

- Conversion
Both the metadata of objects and the data are converted. This is for the scenario where the historical data are not available in the source system (S/4HANA or ERP). After the conversion, the new data will be loaded from the source system into BW Bridge.



There are limits of BW Bridger. (SAP Note xxx)

1 All the bex are gone
2 

![alt text](/Roadmap/images/Future.png?raw=true)

## 2. How to load the data into BW Bridge or DataSphere for the source system(S/4HANA, ERP)

- BW API extractor
- CDSView (ODP)
Pros and Cons:
Fewer customers develop the custom-CDSView including the delta.
The doable solution is to load the data from SAP standard CDSViews. But what is the plan if we want to make enhancement? Are we going to create a custom CDSView by referring to (copying) the SAP standard ones. 

We need to build DataSphere VIEWs on top of the structures of the CDSViews.

- Tables (SLT)
I think this may be the best way. 

