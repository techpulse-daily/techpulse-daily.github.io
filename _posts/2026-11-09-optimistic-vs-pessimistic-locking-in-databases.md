---
layout: post
title: "Optimistic vs Pessimistic Locking in Databases"
description: "Compare optimistic and pessimistic database locking strategies, their performance trade-offs under high load, and how to handle concurrent updates."
date: 2026-11-09
categories: [evergreen]
---

You either start typing in a shared Google Doc and hope nobody overwrites your paragraph, or you lock the entire file so nobody else can touch it.

Databases handle multiple users editing the same record through two strategies called optimistic and pessimistic locking.

## Optimistic Locking

Optimistic locking assumes conflicts are rare, so you read the record and only check if the version number changed when you finally write your changes back. If another transaction updated that same row first, your write fails with a conflict error, and your code has to retry the whole operation from the start.

## Pessimistic Locking

Pessimistic locking takes the opposite approach, placing an exclusive lock on the database row the exact second you read it so nobody else can even look. This prevents update conflicts entirely, but it forces every other user to sit and wait, which destroys your application performance under high load.

## Production Impact

When was the last time an optimistic locking retry loop caused a race condition in your production logs?
