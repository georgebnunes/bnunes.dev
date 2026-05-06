---
date: '2026-05-05'
draft: false
title: 'Did we choose the wrong database model for our new MVP?'
description: "Here are my perks, pains and thoughts on selecting a database model for a new MVP."
summary: "That neverending story about NoSQL vs SQL and the MVP trap"
coverAlt: "Hello world cover image."
tags: ["database", "architecture", "discussion", "track to buy"]
slug: "did-we-choose-the-wrong-database"
---

## Brief Context

We are starting a new Saas project and we are in the early stages of development. We have already decided to use [MongoDB](https://www.mongodb.com/) as our primary database. The team is composed of me and two other developers. 

The [TrackToBuy](https://tracktobuy.com/) project is about tracking products from different stores and alerting users when the price drops. There are other features like grouping them and each group has some sort of budget threshold and once the sum of the products in the group is reached, it will send a notification to the user.

## The Debate

{{< screenshot src="sql_vs_nosql.png" alt="SQL vs NoSQL comparison" >}}

### My Proposal - PostgreSQL
As I saw before hand that the project would have lots of relationships between entities, I proposed using a relational database model, with **PostgreSQL** as our primary database just because this model has some advantages when thinking about relationships, joins, consistency and data integrity.

### Their Proposal - MongoDB
On the other hand, my colleagues prefer a NoSQL database model, with **MongoDB** as our primary database because it is more flexible and we can change the database schema as we go. They also think that it is easier to use and we can develop the project faster. 

<mark>But their main reason was the schema change.</mark> It has to do with the MVP nature of the project. We are not entirely sure about the best way to model the data, so we want to be able to change the database schema as we go. 

These points I tend to agree, but I still think that PostgreSQL is a better choice for this project.

So we end up using MongoDB, despite my poor experience with it in the past.

## Challenges with MongoDB

### Link Related Data
The project has collections with [high cardinality](https://www.mongodb.com/docs/manual/data-modeling/best-practices/) and we have to use referencing over embedding as a model to avoid having large documents. We can't just embed everything because the documents would be too large.

Example: _a group can have multiple products._ 

This may lead to another problem that we are not familiar with in MongoDB, which is **Joins**.

### Joins

Okay, so how are we going to query the data? I have no idea so far! I might figure it out in the next few days. 

I still have something to learn and search about it. Does it MongoDB supports joins?

I was reading about joins in **Document Model** in the Martin's Kleppmann book *Designing Data-Intensive Applications*. And something there caught my attention:

> In document databases such as MongoDB, joins can lead to high latency and query complexity. For example, if you have a collection of orders and each order has an array of product IDs, finding all orders for a specific product would require a separate query for each order. This can be inefficient and time-consuming.

So my question is, does MongoDB supports that? In a way that I don't have to do multiple queries to fetch the data I need? I'm guessing no, but I'm not sure. 

I've heard about the **`$lookup`** operator, but I don't know if it is a good solution for this case. I'll have to read more about it.


### Authentication and Authorization

We also have to think about how to handle authentication and authorization. We were thinking about develop and build our own **service** for that. But it will be time consuming and complex and we wouldn't be able to release our first version as soon as we want to.

So we will use [Supabase](https://supabase.com/) for authentication and authorization. And guess what? **Supabase has postgresql as its primary database**. 😑

{{< screenshot src="supabase.png" alt="Supabase banner" >}}

Is this project turning into a hybrid database model project? I'm starting to think so.

## Conclusion

So yep! We are going with MongoDB, despite my poor experience with it in the past. I'm still not convinced that it is the right choice, but I'm willing to give it a try. 

There will also be the chance to mix with Supabase PostgreSQL to handle auth and maybe other features.

Big big salad! I'm worried with that!

I was also thinking there is space for GraphDBs. Just because in the future we may have to add features like a social network or something similar.

What do you think? Did we choose the wrong database model for our new MVP? Any other option you would suggest?

Feel free to contact me through [Linkedin](https://www.linkedin.com/in/georgebnunes/) and send me a message there! This blog doesn't have comments enabled yet. :(