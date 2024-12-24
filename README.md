# SAP Datasphere

# Description
This repository is an introduction of SAP Datasphere, a data warehouse platform built on the SAP Business Technology Platform (SAP BTP).

# Overview
Two years ago, SAP Datasphere was introduced. I was tasked with exploring its features to determine how we could leverage it to address the pain points within our existing SAP BI solution, which relies heavily on ABAP CDS views created in the S/4HANA called embedded analytics.

I delved into SAP Datasphere and developed some Proof of Concepts (POCs). Unfortunately, I did not keep the detailed records at that time. Since I have some time now, I revisited the tool and documented my insights and thoughts here. Hope this documentation will help you gain a better understanding of SAP Datasphere.


# Requirements
You can get 30days free trial version of SAP Datashpere.
[Here](https://www.sap.com/products/technology-platform/datasphere/trial.html)

# Contents

SAP has already ownered many good BI products and solutions E.g.

On-premises: BW(BWonHANA or BW/4HANA), HANA, BusniessOjbect

On-cloud: DWC, HANA Cloud, SAC

Datasphere is very similar to DWC. But it is an upgrade version of DWC, called SAP data fabric. Like Micrsoft Fabric (formerly known as Azure Synapse Analytics), it offer similar capabilities for integrating, managing, and analyzing data from various sources.

Business Scenarios:

👉 In retail business, we want to analyze the relationship between the store traffic data(3rd party) and the marketing campaign data(SAP CRM). 

👉 We have the devliery date in SAP(ERP/SD) system. We also want to confirm the goods arrival time by referrring to the travel information. 

👉 We collect the stream data from the production lines and try to adjust the production plan in SAP(PP) system. 

👉 We plan to perform the machine learning.

To suport the business requirements, SAP Datashere provides the following features 
1. 
