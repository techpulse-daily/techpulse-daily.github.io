---
layout: post
title: "Why SELECT * Hurts Performance and How to Fix It"
description: "Learn how using SELECT * forces the database to read all columns, increases latency and CPU work, and prevents index use, and see why selecting only needed columns improv"
date: 2026-08-29
categories: [evergreen]
youtube_id: bhTnhORqXWA
---

Ordering everything on the menu when you only wanted a cup of coffee sounds wasteful, and SELECT * is the same for databases. When you write SELECT * FROM orders, the database pulls every column— even ones you never use— just like a server brings the whole menu to your table. Each extra column is data you don’t need, adding network latency— the time it takes for data to travel— and CPU work— the processor cycles spent parsing. Indexes— small, sorted lookup tables that speed searches— can’t help because the query still reads every row’s full record. The result is slower page loads, higher memory consumption, and more I/O— the reading and writing of data to disk. By specifying only the columns you actually need, you shrink the data packet, let indexes do their job, and free up resources for other users. That’s why SELECT * turns a simple order into a heavy‑weight operation. Now you understand that fetching all columns is like ordering the entire menu when you only wanted coffee.

Can you recall a time when trimming a SELECT to needed columns noticeably improved a page's load time?

## Ordering everything when you only need coffee

SELECT * pulls all columns like a full menu order

## How the analogy maps to SQL

Each column equals a menu item; extra items waste time

## Why it slows queries

Unneeded data adds network latency and CPU parsing

## Indexes lose their edge

Full rows bypass index shortcuts, forcing full scans

## The practical impact

Higher memory use, slower pages, more disk I/O
