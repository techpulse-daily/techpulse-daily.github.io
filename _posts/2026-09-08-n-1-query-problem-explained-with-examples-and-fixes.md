---
layout: post
title: "N+1 query problem explained with examples and fixes"
description: "Learn what N+1 queries are, how they slow down apps, and how to eliminate them using joins and eager loading for faster pages."
date: 2026-09-08
categories: [evergreen]
---

Sending a runner back to the store 100 times for 100 items instead of handing them a full list sounds absurd—but that's exactly what N+1 queries do to your app. An N+1 query problem occurs when your code asks the database (the storage system for your data) for a list of rows, then for each row makes another separate request for related data. The first request is the “1”, the many follow‑up requests are the “N”. Each extra round‑trip adds latency, so a page that could load in a fraction of a second stalls while the database processes dozens or hundreds of tiny queries. The fix is to fetch everything you need in one go, using techniques like joins (combining tables in a single query) or eager loading (pre‑loading related data). By consolidating queries you reduce network chatter, lower server load, and keep users from waiting. When you spot a pattern of repeated lookups, you’ve likely found an N+1 hidden killer. Now you know that a single, well‑crafted query can replace a flood of tiny requests, keeping your app fast and responsive.

Can you recall a time when a page felt sluggish and you discovered an N+1 query was the cause?

## Runner goes back 100 times for 100 items

Analogy of inefficient fetching that mirrors N+1 queries.

## Mapping: One list, many extra lookups

First query gets list, then each item triggers its own query.

## Why it slows you down

Each extra query adds network latency and database load.

## How to stop it

Use joins or eager loading to fetch all needed data at once.

## Impact of fixing N+1

Faster pages, lower server cost, happier users.
