---
layout: post
title: "How Load Balancers Work: Traffic Distribution and Health Checks"
description: "Learn how load balancers distribute web traffic across server infrastructure using routing algorithms, real-time health checks, and capacity metrics."
date: 2026-11-05
categories: [evergreen]
youtube_id: gDwoG7KRdLA
---

The host at a bustling restaurant waves you to the next free chef, keeping diners moving.

In a web service, that host is a load balancer. It routes incoming traffic the way a restaurant host directs orders to chefs, using a distribution algorithm – the rule it follows to spread work. The analogy helps illustrate the core responsibilities of a load balancer without adding any new facts.

## How the load balancer selects a server

Just as a host checks which chef has the shortest queue, a load balancer checks each server’s real‑time load. It looks at how many requests a server is handling versus its capacity and then picks the least busy. This simple decision logic keeps the overall system responsive, because no single server becomes a bottleneck while others sit idle.

## Handling failures automatically

When a chef steps away or a station breaks down, the restaurant host stops sending new orders there. Likewise, a load balancer runs a health check – essentially a ping test – on each backend server. If a server fails the check, the balancer automatically notices and stops sending traffic to that server. The failed node is taken out of rotation without human intervention, preserving uptime for the rest of the pool.

## Request flow from client to server

A user request travels from the internet to the load balancer. The balancer may be a hardware appliance or a cloud service; the implementation detail does not change the logical flow. After the health check and selection steps, the request is routed to the chosen server. The server processes the request and sends the response back through the same balancer, which forwards it to the client. This round‑trip mirrors a diner’s order being taken, cooked, and delivered by the chef who was assigned the task.

## When the balancer becomes a problem

Even with a good algorithm, the load balancer can still cause performance issues. If the distribution logic sends a disproportionate amount of traffic to one server, that server can become overloaded while others remain underutilized. The symptom is a slow‑loading page. The first diagnostic step should be to check whether the load balancer is sending traffic to an overloaded server. If it is, adjusting the algorithm or scaling the backend pool can restore balanced performance.

Understanding the load balancer’s role clarifies why it matters for reliability and latency. It is the single point that decides where work goes, monitors server health, and shields clients from individual server failures. When the balancer functions as intended, the system behaves like a well‑run kitchen: orders flow smoothly, chefs are never idle or overwhelmed, and diners leave satisfied. When it fails to distribute load evenly, the experience degrades, and the underlying cause is often the balancer’s configuration rather than the application code itself.
