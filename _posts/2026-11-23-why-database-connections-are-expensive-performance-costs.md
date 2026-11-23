---
layout: post
title: "Why Database Connections Are Expensive: Performance Costs"
description: "Learn why opening database connections for every web request drains server CPU and memory, and how connection pools solve this performance bottleneck."
date: 2026-11-23
categories: [evergreen]
---

Four‑step entry

Every visitor must line up, flash a badge, and complete a four‑step handshake before a single question is answered.

Database link

That ritual is a database connection — a link between your code and the data store that costs time and resources and often limited.

Setup steps

Opening one forces the driver to authenticate, allocate a network socket, and negotiate protocols, each step consuming CPU cycles and memory.

Server stalls

If you repeat this for every user click, the server stalls, just like a line of people waiting for the same security desk daily.

Connection pool

A connection pool keeps a handful of ready‑made handshakes, handing one out instantly, then returning it after use.

Your experience?

When did a slow page make you consider adding a pool to your app?

Right‑sized pool

Most production systems use pools sized to match concurrent users, avoiding both starvation and wasted connections.

## Why a database connection feels like a security checkpoint

Think of a database connection as a security desk at a building entrance. Each visitor must present credentials, wait for an officer to verify identity, and then be granted access. In software terms, that “verification” involves the driver authenticating the user, allocating a network socket, and negotiating the communication protocol. Each of these steps consumes CPU cycles and memory on both client and server. The cost is real; connections are a finite resource, and establishing them repeatedly adds measurable latency.

## The cost of handling every request individually

If every click on a web page triggers a fresh connection, the server quickly becomes a bottleneck. Imagine a line of people all waiting for the same security desk; the throughput drops dramatically, and response times balloon. The same thing happens when an application opens a new connection for each request: the server spends more time setting up and tearing down sockets than processing actual business logic. This leads to higher CPU usage, more memory pressure, and ultimately slower page loads for users.

## How a connection pool solves the problem

A connection pool is essentially a small group of pre‑established handshakes sitting idle, ready to be handed out the moment a request arrives. When a thread needs a connection, it pulls one from the pool, uses it, and returns it. Because the expensive setup steps have already been performed, the handoff is virtually instantaneous. The pool also caps the number of simultaneous connections, preventing the server from exhausting its resources.

## Sizing the pool correctly

The pool should be sized to match the peak number of concurrent users your system expects. Too small, and requests will queue for a connection, re‑introducing latency. Too large, and you waste memory and file descriptors on idle connections. In practice, most production systems tune the pool based on observed concurrency, striking a balance that avoids both starvation and excess.

## When to consider adding a pool

If you notice slow page loads that correlate with spikes in traffic, the symptom is often the overhead of repeatedly establishing connections. Adding a pool, or adjusting its size, can reduce that overhead dramatically. The decision point is simple: if a single request feels sluggish because the application is spending time handshaking with the database, a connection pool is the pragmatic fix.
