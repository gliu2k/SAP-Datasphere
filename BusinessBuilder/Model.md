# Business Builder 

It is a tool designed for **business users** to create their own models from the business perspectives.

<pre>😊 Honestly, I am not sure if it can work as expected. In my experience, I have not encountered this before. 
   It is quite challenging for business users to create ad-hoc queries.</pre>

![alt text](/BusinessBuilder/images/BB.png?raw=true)

## 1. Create Business Entities

![alt text](/BusinessBuilder/images/Arch.png?raw=true)

- **Dimension** and **Fact** Entity

Both kinds of business entities must be created on top of the existing **Data Builder** objects(tables or views). 

> [!NOTE]
> As all the business objects are supposed to be created by the business users, they only have limited functionalities, filter or association, to operate on the data. All the complex logic must be done in the **Data Builder** objects. 

In the **Fact** entities, add the **Dimension** entity as the attributes of the entity
![alt text](/BusinessBuilder/images/Entities.png?raw=true)

## 2. Create new Fact Model or Consumption Model 

## 2.1. Insert the **Fact** entity 
![alt text](/BusinessBuilder/images/CM1.png?raw=true)

## 2.2. Select the fields to expose either from the Fact entity or its associated Dimension entity
![alt text](/BusinessBuilder/images/CM2.png?raw=true)

## 2.3. Create the perspectives (option)
![alt text](/BusinessBuilder/images/QRY.png?raw=true)

<pre> It feels very similar to creating a query for me. </pre>

## 2.4. A Complex Sample

This is a little complex **Consumption Model**. Two **Fact** entities are linked by the same associated **Dimension** entity.

![alt text](/BusinessBuilder/images/ComplexCM.png?raw=true)



