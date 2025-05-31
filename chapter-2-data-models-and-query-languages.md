## Introduction

Focus on:

1. Why data model matters
2. why query language matters

Takeaway:

There’s no one size fits all. Choose based on how your app uses the data. 
>>  Your data model should be driven by your application’s access patterns.

in short, data model (how it should look/structure) , and how to retrieve it why it matters. As this will help you in your architecture decisions. 

## Types of models:

Picking model (structure) of the data helps in : how easy it is to query , how quickly it will evolve, performance under the load.

eg: In book, we have bill gates resume and now the task is to store into DB. Now, as an dev which data model you will pick? 

**1. Relational (tables and rows) eg: MySQL**

- table and rows 
- use keys 
- Sql (query language)

**Pros:**

1. Oldest and strongest (lol)

2. Joins are easy and powerful

3. data is nomarlized

**Cons:**

1. changing schema is a pain

2. Joins (complex) can be expensive

Use: where you need joins

**2. Document (documents and collections) eg: MongoDB**

- pages or collections
- NoSQL
- JSON like strcuture

**Pros:**

1. Schema is flexible, easy to scale

2. Faster reads (no joins)

3. Amazing for nested data

**Cons**

1. Harder to update consistently 

2. Duplication is easier here 

use: deeply nested data /documents

**3. Graph (Nodes and edges) eg: Neo4j**

When the relationships are complex then Grpah DB comes in picture. Relationship heavy 

social media apps, recommendation apps, etc,

Think of  where you want to target the connection of connection (eg: your friend like XX product)

- nodes and edges 

use: connections

## Query language

How easy we can query the data.

1. SQL : strong consistency, ACID, rich queries

2. NoSQL : Fast look ups

3. GraphQL : Leave it on client

## connection with principles:

1. Reliable

2. Scalable

3. Maintainable


### can we merge these all 3 db? 

yes, we can. In large scale applications you can split the data between the different data storage system.

Eg: ecommerce website, 

Tables: breaking the users, orders, products

Document: per user/detail

Graph: Recommendation


