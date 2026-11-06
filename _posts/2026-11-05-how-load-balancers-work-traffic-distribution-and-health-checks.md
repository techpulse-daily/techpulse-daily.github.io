---
layout: post
title: "How Load Balancers Work: Traffic Distribution and Health Checks"
description: "Learn how load balancers distribute web traffic across server infrastructure using routing algorithms, real-time health checks, and capacity metrics."
date: 2026-11-05
categories: [evergreen]
---

The host at a bustling restaurant waves you to the next free chef, keeping diners moving.

That host is a load balancer, directing web traffic just like orders to chefs using a distribution algorithm -- the rule it follows to spread work. It checks each server's real-time load -- how many requests it's handling versus its capacity -- and picks the least busy. If a server goes down, the balancer automatically notices the failed health check -- a simple ping test -- and stops sending traffic there.

A user request travels from the internet, hits the load balancer -- which may be a hardware appliance or cloud service -- then routes to the chosen server, and the response returns the same way.

## Limits of the Analogy

While the restaurant host analogy explains the basic routing function, it breaks down under the realities of distributed systems. A human host has conversational context, can judge portion sizes, and manages physical queues in a single room. A load balancer operates purely on stateless protocols, packet headers, and metric thresholds across geographically dispersed data centers. The analogy also fails to capture session persistence, where certain requests must return to the exact same server to maintain state, something a restaurant host would handle by seating returning customers with the same waiter.

## Operational Impact

When your page feels slow, have you checked whether the load balancer is sending traffic to an overloaded server, and page load time drops?

Understanding how your load balancer distributes traffic is a fundamental troubleshooting step. Misconfigured distribution algorithms or failing health checks often mask underlying capacity issues. Verifying that the least busy server metric is functioning correctly prevents cascading failures across your infrastructure fleet.
