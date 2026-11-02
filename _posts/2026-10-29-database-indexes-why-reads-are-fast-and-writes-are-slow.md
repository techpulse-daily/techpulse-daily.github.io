---
layout: post
title: "Database Indexes: Why Reads Are Fast and Writes Are Slow"
description: "Learn how database indexes speed up searches while slowing down write operations through structural maintenance, page splits, and B-tree updates."
date: 2026-10-29
categories: [evergreen]
---

Every new book forces the librarian to update five separate catalogues before finally shelving it.

Databases face the exact same penalty when you add an index, which is a sorted lookup guide built to speed up searches. When a user logs in, the database skips scanning millions of messy rows and jumps straight to the right address. Writing data brings the system to a crawl because every single index needs a rewrite to keep its pointers accurate.

## Where the Analogy Holds

The librarian analogy maps directly to disk I/O and B-tree maintenance. Just as a physical library card catalog requires manual sorting and filing for every new volume, a database index must maintain strict sort order. When you insert a row into a table with three indexes, the storage engine does not just write the base table. It also updates the root and leaf nodes of three separate sorted structures. This structural maintenance is why writes pay a steep performance price.

## Where the Analogy Breaks Down

A human librarian works sequentially and feels fatigue, whereas a database engine processes concurrent disk or memory operations. However, the physical bottleneck remains similar. Random I/O during index updates causes page splits, forcing the storage engine to allocate new blocks and rearrange pointers. While a human might stack books on a desk to process later, a database must maintain consistency immediately, locking index pages and increasing contention across transactions.

## Why It Matters in Production

You trade slow writes for fast reads every single time you need instant search results on a heavy table. Unchecked index growth quietly degrades insert and update throughput until application latency spikes during peak traffic.

How many indexes are currently slowing down user registration on your most critical production tables right now?
