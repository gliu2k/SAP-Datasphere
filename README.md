# SAP Datasphere

# Description
This is my journey of learning the SAP Datasphere product.

# Overview
Two years ago, SAP Datasphere was introduced. I was tasked with exploring its features to determine how we could leverage it to address the pain points within our existing SAP BI solution, which relies on ABAP CDS views in the S/4HANA called embedded BW solution.

I delved into the product and developed Proof of Concepts (POCs). Unfortunately, I did not keep detailed records. Now that I have some time, I want to revisit this product and document my insights and thoughts here.

The product continues to evolve, and my understanding may not be entirely accurate. However, I hope this documentation will help you gain a better understanding of SAP Datasphere.

# Requirements
You can get 30days free trial version of SAP Datashpere.


# 1. Getting Started
I alwasy want to ask some questions in learing something new.

Q1:
SAP has ownered many good BI products and solutions E.g.
On-premises- BW(BWonHANA or BW/4HANA), HANA, BusniessOjbect<BR>
On-cloud - HANA Cloud, Data Warehouse Cloud, SAC. S/4HANA Cloud

Who does SAP want to launch a new BI product? And why does SAP name it as SAP Fabric? At the meaning time, Microsfot has released its Data Fabric product in Azure? Are they similar? 

A1:
Yes, they are similar. They both try to combine the data from the traditional BW system with other data, structured and unstructured, from the 3rd party systems either on-Promise or on-Cloud.

In retail business, we want to analyze the relationship between the store traffic data and the marketing campaign data(SAP CRM). We have the devliery date in SAP ERP(SD) and also want to confirm the goods arrival time by referrring to the travel information. We want to collect the realtime data from the production lines and adjust the production plan in SAP ERP system. We want to do data analysis or machine learning on both SAP data and other data.

The Data Fabric is the product to meet the requirments in these buiness senarios. We can see the features like stream, python, data science(ML/AI) and pipelines are supported in the cloud product.

If we are going to go for SAP Datasphere, we probably need to ask the following questions:

- Are we going to move to cloud?
- How much business data are in SAP systems currently?
- Do we need to ingest data from non-SAP system? If yes, what is the percentage?
- What benefit can it (data combination) bring to the business? 

# 2 SAP Datashpere

