# SAP Datasphere


# Description
This repository is an introduction to SAP Datasphere, a data warehouse platform built on the SAP Business Technology Platform (SAP BTP).


# Overview
Two years ago, SAP Datasphere was introduced. I was tasked with exploring its features to determine how we could leverage it to address the pain points within our existing SAP BI solution, which relies heavily on ABAP CDS views known as embedded analytics in S/4HANA system.

I dived into SAP Datasphere and developed some Proof of Concepts (POCs). Unfortunately, I did not keep the detailed records at that time. Now that I have some time, I revisited the tool and documented my insights and thoughts here. Hope this documentation will help you gain a better understanding of SAP Datasphere.


# Requirements
You can get 30days free trial version of SAP Datasphere from [here](https://www.sap.com/products/technology-platform/datasphere/trial.html).

# Contents

SAP already possesses many good BI products and solutions **E.g.**

**On-premises: BW(BWonHANA or BW/4HANA), HANA, BusinessObject**

**On-cloud: DWC, HANA Cloud, SAC**

SAP Datasphere is very similar to SAP DWC. But it is an upgraded version of SAP DWC, called SAP data fabric. Like **Microsoft Fabric** (formerly known as **Azure Synapse Analytics**), it offers similar capabilities for integrating, managing, and analyzing data from various sources.

### Business Scenarios

👉 In retail business, we want to analyze the relationship between the store traffic data(3rd party) and the marketing campaign data(SAP CRM). 

👉 We have the delivery date in SAP(ERP/SD) system. We also want to confirm the goods arrival time by referring to the travel information. 

👉 We collect the stream data from the production lines and try to adjust the production plan in SAP(PP) system. 

👉 We plan to perform the machine learning.

To support the business requirements, SAP Datasphere provides the following features 

### 1. Administration
- [Admin](Admin/Admin.md)
  
### 2. Data Builder
- [Model](DataBuilder/Model.md)
- [Flow](DataBuilder/Flow.md)
  
### 3. Business Builder
- [Model](BusinessBuilder/Model.md)
  
### 4. Data Integration Monitor
- [Monitor](Integration/Monitor.md)

### 5. Roadmap
- [Roadmap](Roadmap/Roadmap.md)

> [!CAUTION]
> You may encount **403 Forbidden** after clicking some hyperlinks. Please copy and open the URL in a new browser tab.
