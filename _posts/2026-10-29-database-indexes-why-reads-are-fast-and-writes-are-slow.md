---
layout: post
title: "Database Indexes: Why Reads Are Fast and Writes Are Slow"
description: "Learn how database indexes speed up searches while slowing down write operations through structural maintenance, page splits, and B-tree updates."
date: 2026-10-29
categories: [evergreen]
youtube_id: PtN3_wsvPNk
---

Every new book forces the librarian to update five separate catalogues before finally shelving it.

Databases face the exact same penalty when you add an index, which is a sorted lookup guide built to speed up searches. When a user logs in, the database skips scanning millions of messy rows and jumps straight to the right address. Writing data brings the system to a crawl because every single index needs a rewrite to keep its pointers accurate.

## Where the Analogy Breaks Down

The physical library analogy helps visualize the cost, but databases operate under different constraints. A library catalogue uses physical cards in wooden drawers that require manual labor to rearrange. A database index uses data structures like B-trees that split and rebalance automatically on disk or in memory. However, the fundamental trade-off remains identical. Computational work replaces physical labor, but the CPU cycles and disk I/O required to update sorted pointers still consume finite system resources.

## Why This Trade-Off Matters in Production

You trade slow writes for fast reads every single time you need instant search results on a heavy table. System architects often add indexes indiscriminately to solve slow query alerts without measuring the impact on concurrent transactions. Every index added to a table increases the overhead on INSERT, UPDATE, and DELETE operations because the database engine must maintain consistency across every lookup guide simultaneously.

Check your table indexes. How many indexes are currently slowing down user registration on your most critical production tables right now?
