---
date: '2026-07-16'
draft: false
title: 'Choosing Supabase as an external authentication service'
description: "Build one from scratch is not feasible so we decided to integrate with Supabase"
summary: "We're running out of time! Supabase now, develop an authetication service later"
coverAlt: "Authentication"
tags: ["database", "architecture", "discussion", "authentication", "supabase", "track to buy"]
slug: "supabase-authentication"
---

Just like any other SaaS or app platform, we need to manage user access. We'd like to give a custom experience for our users on our platform. To achieve that, each user must hold an account. And to hold this account, we must provide features of authentication and authorization.

This is an MVP app, and we are in a hurry to validate with our users as soon as possible. So, there is no time for us to develop an effective auth solution from scratch. Of course, it would be better to have one on our shelf and reuse it as we like, and then we find ourselves in doubt.

We were in doubt whether we should go and build one or just take one ready to use from the market.

In the end, we pick a SaaS named Supabase.

# Why not use Auth.js

Our frontend application was developed in Next.js and of course we could use Auth.js to help us to add social login and integrate with providers like Google and Apple. But what happened was, at some point in the documentation of Auth.js we saw that a database was necessary in order to implement it with Next.js and there we found a problem: we don't have a database server ready to use. We don't have enough budget to run and keep running an EC2 instance in AWS with a database server or pay for an RDS instance. 

Using Auth.js, would become an expensive implementation for our MVP app

# Why we said yes to Supabase?

After a quick research, we found Supabase. And at first look, we saw that it solves all of our two major problems:
- Authentication
- Database infrastructure

Supabase free-tier offers useful features for our MVP app like those ones described up next.

## Social Login

It help us to integrate with Google and Apple accounts for authentications. We don't want our users to fill long forms and worry about passwords, at least for now.

Supabase has everything ready for us to use. Only a couple config files and it is done.

## Database
Supabase also has a database schema ready for this kind of feature to help us manage sessions and other data.


# Supabase cons

The thing here is minimal; all we wanted was to have a customized domain name. And the free tier doesn't allow you to customize that.

The free tier has limitations, and that is totally acceptable! We are now getting familiar with startup costs, and to host something like that on the cloud definitely has a price for it.


## Impact on hosting
Our app was running on S3 buckets. We were using that feature that hosts static websites. But when we added Supabase, it affected our infrastructure, and now we have to move to some containerized solution in order to run our app.

This will increase our cost; we are now running our containers in a free service like Google Run.

# Conclusion
For now we are going to use Supabase, but just for now. Of course in the future we'll be building our own auth service with our own rules and features or at least searching for alternatives like "Keycloak".