---
layout: post
title: "Why Postgres COUNT(*) Is Slow: MVCC and Table Scans"
description: "Learn why relational databases like PostgreSQL must scan every row for total counts due to MVCC visibility rules and lack of a master counter."
date: 2026-10-19
categories: [evergreen]
youtube_id: Fi7C1NI4jbI
---

A librarian cannot tell you how many books the library owns without walking down every single aisle to tally them.

## Why Relational Databases Scan the Table

Relational databases like Postgres do the exact same thing whenever you write a query asking for a total row count. They rely on MVCC, multiversion concurrency control, a design where the database keeps distinct copies of records so different users can read and write simultaneously.

To calculate the total, the database engine inspects your transaction snapshot, loads pages from disk into memory, and verifies whether each row is visible to your session. Because of those visibility rules, there is no master counter, turning a simple count on ten million rows into ten million individual disk checks.

## The Cost in Production

This architecture explains why simple operations can become expensive bottlenecks in production systems. When a query requests a total count, the database cannot simply read a stored metadata value. It must perform a full scan.

What is the slowest dashboard you have ever used that turned out to be running a total row count on every single page refresh?
