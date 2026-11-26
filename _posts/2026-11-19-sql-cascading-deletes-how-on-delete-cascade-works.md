---
layout: post
title: "SQL Cascading Deletes: How ON DELETE CASCADE Works"
description: "Learn how SQL cascading deletes prevent orphaned records by automatically removing related child rows in foreign key relationships when a parent row is deleted."
date: 2026-11-19
categories: [evergreen]
youtube_id: P-LbVSEFry8
---

You close a customer's account and all 400 orders and 2,000 receipts disappear instantly.

## Cascading Delete Explained

That is cascading delete—a rule that automatically removes all related rows when a parent row is deleted, preventing stray data. The database defines a foreign key—a link field that points from orders to the customer—and marks it with ON DELETE CASCADE. Because the database does the work in a single transaction, the delete runs faster than issuing separate commands.

## Orphaned Rows Cause Trouble

If the foreign key lacks the cascade flag, deleting the customer leaves orphaned orders and receipts, which can cause query failures and waste storage. When this happens, you have to clean the leftover rows manually.

## Enable Cascade Rule

Add ON DELETE CASCADE to the foreign key definition, and the database will propagate the delete automatically.
