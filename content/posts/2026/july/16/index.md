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

