---
layout: post
title: "UUID vs Sequential IDs: How Universally Unique Identifiers Work"
description: "Learn how 128-bit UUIDs eliminate database primary key collisions and enable distributed systems to generate unique identifiers without central coordination."
date: 2026-10-26
categories: [evergreen]
youtube_id: 37QVK8E06Tc
---

Two factories on different continents can print the exact same thirty-six-character serial number for decades without ever colliding.

## The Mechanism of Uniqueness

That is a UUID, which stands for Universally Unique Identifier, a randomly generated string of letters and numbers designed to never repeat anywhere. A UUID solves this by using massive randomness, packing one hundred twenty-eight bits of data into thirty-six characters so probability handles uniqueness. Because the space of possible values is so astronomically vast, you can generate a billion IDs every second for a century and never see a duplicate.

## Where Traditional Methods Fail

Most databases rely on auto-incrementing integers, counting up from one, which requires a central authority to hand out each next number in order. That central counting method fails the moment two separate servers try to create a new database row at the exact same millisecond.

## Operational Impact

When was the last time a primary key collision forced you to rewrite a database migration on a live production system?
