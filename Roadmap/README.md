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

- BW SAPI Extractor
- CDSView (Extractor ODP)
- Tables (SLT)
  
Pros and Cons:

- Fewer customers develop the custom-CDSView including the delta.
[Example](https://github.com/SAP-samples/teched2022-DA281/blob/main/exercises/dd1/README.md)

The doable way is to load the delta data from SAP standard CDSViews. 
[HowTo]
When we want to make enhancements, are we going to create a custom CDSView by referring to (copying) the SAP standard ones?

And, we need to rebuild the DataSphere **VIEWs** on top of these CDSViews structures.

- I think this may be the best way. The workload is almost the same as using CDSViews. Most starndard CDSViews are very simple. But it is very flexiable.  

