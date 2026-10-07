---
layout: post
title: "Database Query Caching: Stale Data and Invalidation"
description: "Learn how database query caching improves application performance while introducing stale data risks, and discover strategies for proper cache invalidation."
date: 2026-10-07
categories: [evergreen]
---

The gym scoreboard photocopy handed out every ten minutes while the real game score keeps changing.

## The Purpose of Caching

That photocopy is a cache, a saved copy kept close by so your app stops asking the database for the exact same expensive answer over and over. When a user requests rows of data, the system checks this temporary storage first before running the heavy query.

Speed is the whole reason we accept the trade-off. Milliseconds matter when thousands of people hit your shop at once.

## When the Data Lies

But the moment someone scores a point in reality, the paper sheet in your hand is lying because it shows the past. This stale data bug happens every time the underlying records change without clearing out that saved copy.

When was the last time your app showed old prices because a background worker forgot to invalidate the cache?
