# Data Builder
![alt text](/images/1.png?raw=true)

In fact, it contains not only the models componetes but also ETL compoenets.In this section, I will focus on the data modeling part.

## Tables

![alt text](/images/Tables.png?raw=true)

You can create the local tables, or create a local table by importing from CSV file, or create the remote tables. 

In creating the local table, you need to speciy the sematic types which include

Remote tables: it is like HANA-SDA or the “link” concept in Azure Fabirc. It is a virtual object which maps to the physical object located in the remote system. E.g. S/4HANA(on premise)

 
You can create local tables (or create from CSV file) or import remote tables. 


### Semantic Usage:
![alt text](/images/NewTable.png?raw=true)

-	Fact: Transaction Data, used for Analyitcs Model
-	Dimension/Text/Hiearchy: master data, used for the assocication 

### Assocation: defined the attributes of a dimension table



### Delta Capture
![alt text](/images/TableDelta.png?raw=true)
Two tables will be genated when the “Delat Caure” flag is turned on.

Comparing to the active table, additional two fields are added into the delta tables. The change type can be I (initial), D(delete), U(updated) in the same records after ceterain acitivtiies take place.



## Views
![alt text](/images/Views.png?raw=true)

### SQL View

### Graphics View
![alt text](/images/NewGV.png?raw=true)

Graphics View – Simparly to HAAN Calcaultion View
1.	It is sematic type as well. Ony the fct can be used in the Anslyistics
2.	Attributes is the same to columns in HANA view
3.	Import Parameters, same as in HANA view. You can push it to low node to improve performance and then map it to the variables crated in the analytic model
Join, Filter and projection(to show/hide colums) , Aggretion Node.


## ER Models
![alt text](/images/NewGV.png?raw=true)



## Analytic Models
![alt text](/images/NewGV.png?raw=true)

## Currency Conviersion View
![alt text](/images/NewGV.png?raw=true)

## Data Access
![alt text](/images/NewGV.png?raw=true)




