---
layout: post
title: "Hot Rows in Databases: Fixing High-Concurrency Update Contention"
description: "Learn how database lock contention occurs during high-volume updates on a single hot row and discover engineering strategies to scale flash sales."
date: 2026-10-09
categories: [evergreen]
---

Forty thousand fans must pass through a single turnstile to enter the sold-out stadium.

## The hot row problem

In databases, this is a hot row, where every single incoming request tries to update the exact same record at the same exact time. When a ticket sale or flash sale drops, thousands of threads grab for that single row in your database table.

## Database locks and failures

The database uses a lock -- a temporary exclusive hold that lets only one process touch the record while others wait. While that first thread updates the balance, forty other threads time out and your application throws connection errors.

## Mitigation and review

Engineers fix this by splitting that single record into multiple counters, or using a cache -- a saved copy kept close by -- to batch the updates before hitting disk.

What specific database query in your current project makes thirty different threads fight for the exact same row right now?
