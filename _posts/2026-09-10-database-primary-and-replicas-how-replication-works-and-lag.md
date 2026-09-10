---
layout: post
title: "Database Primary and Replicas: How Replication Works and Lag"
description: "Learn how a primary server writes data and replicas stay synchronized, how read traffic is distributed, and the impact of replication lag on availability."
date: 2026-09-10
categories: [evergreen]
---

The CEO writes the company updates, and five assistants copy them to read to teams. In databases, the CEO is the primary server – the source of truth where all writes happen. The assistants are replicas – read‑only copies that stay in sync with the primary. When the primary records a new update, it immediately tells each replica to apply the same change, so every team hears the same news at nearly the same time. This setup spreads read traffic across many machines, reducing load on the primary and preventing it from becoming a bottleneck. If one replica goes down, the others still serve data, keeping the system available. However, because replicas lag slightly behind the primary, a read might return slightly outdated information – a trade‑off called replication lag. Understanding this helps you decide when to prioritize fast reads over absolute immediacy, and how to design failover strategies for reliable services.

When have you relied on a replica for read queries, and how did replication lag affect your user experience?

## CEO Writes, Assistants Copy Updates

Primary server creates data; replicas duplicate it for others

## How Replication Mirrors the Process

Primary pushes changes; each replica receives and stores the same

## Why Use Replicas

Distribute read load, keep system responsive under heavy traffic

## When Replication Falls Short

Replica lag means reads may see slightly old data

## Impact on System Design

Choose replication to balance speed, availability, and data freshness
