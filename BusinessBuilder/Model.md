# Business Builder 

It is a tool designed for **business users** to create their own models from the business perspectives.

<pre>Honestly, I am not sure if it will work as expected. Creating ad-hoc queries can be quite challenging for the business users.😊 </pre>

![alt text](/BusinessBuilder/images/BB.png?raw=true)

## 1. Create Business Entities

![alt text](/BusinessBuilder/images/Arch.png?raw=true)

- **Dimension** and **Fact** Entity

Both kinds of business entities must be created on top of the existing **Data Builder** objects(tables or views). 

> [!NOTE]
> As all the business objects are supposed to be created by the business users, they only have limited functionalities, like filter and association, to operate on the data. Thus, the complex logic must be done in the **Data Builder** objects. 

In the **Fact** entities, add the **Dimension** entity which includes the attributes of the entity member

The  **Dimension** will be available in creating the Fact/Comsumption Model.
![alt text](/BusinessBuilder/images/Entities.png?raw=true)

## 2. Create new Fact Model or Consumption Model 

### 2.1. Insert the **Fact** entity to create a Consumption Model 
![alt text](/BusinessBuilder/images/CM1.png?raw=true)

### 2.2. Select the fields to expose either from the Fact entity and its associated Dimension entity
![alt text](/BusinessBuilder/images/CM2.png?raw=true)

### 2.3. Create the perspectives (optional)
![alt text](/BusinessBuilder/images/QRY.png?raw=true)

<pre> It is very similar to creating a query on the consumption model. </pre>

### 2.4. A Complex Sample

This is a little complex **Consumption Model**. Two **Fact** entities are linked by the same associated **Dimension** entity.

![alt text](/BusinessBuilder/images/ComplexCM.png?raw=true)



