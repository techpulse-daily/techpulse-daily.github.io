---
layout: post
title: "SQL Foreign Keys Explained: Preventing Orphaned Data"
description: "Learn how database foreign keys enforce referential integrity between tables to block invalid deletions and prevent orphaned production data."
date: 2026-10-06
categories: [evergreen]
---

A hotel front desk refuses to delete room three hundred twelve while a guest is still sleeping inside.

## How Foreign Keys Connect Tables

Databases do the exact same thing using a foreign key, which is a rule connecting two separate tables so neither can break. Imagine an orders table pointing directly to a customers table through a shared identification number.

## Database Enforcement and Manual Checks

If you try deleting a customer who still has active orders, the database throws an error and blocks the query. Without this built-in protection, your application code has to manually check every single related record beforehand.

## Preventing Orphaned Data

When was the last time a missing database rule let orphaned data slip into your production tables?
