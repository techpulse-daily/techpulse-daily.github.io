---
layout: post
title: "Database lock explained: how locks work and impact performance"
description: "Learn what a database lock is, the difference between read and write locks, how they cause slow pages, and steps to diagnose and resolve lock‑related performance issues."
date: 2026-10-01
categories: [evergreen]
youtube_id: fcf075OeSek
---

Only one key opens the coffee shop bathroom, so everyone else waits.

## How database locks work

That waiting line is a database lock – a control that lets only one transaction edit data at a time. When a user starts to update a row, the database places a lock, like handing the bathroom key to that person. The lock prevents two people from writing conflicting changes, just as two people in the bathroom would create a mess.

Databases also offer shared locks, letting many readers view data simultaneously while still blocking writers, like letting several people peek through the bathroom door but not enter.

## Where the analogy breaks down and why it matters

If two transactions each wait for the other's lock, they block each other—a deadlock, like two people each holding half the bathroom key and refusing to step out.

Have you ever seen a page freeze because the server was waiting for a lock to release?
