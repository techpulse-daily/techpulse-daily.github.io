---
layout: post
title: "Database Time Zone Bugs: UTC Storage and Offset Errors"
description: "Learn how database timestamp offset errors and server local clock mismatches cause incorrect date shifts, and how to fix UTC storage bugs."
date: 2026-10-06
categories: [evergreen]
---

An online order placed at eleven PM in London shows up in the database as tomorrow morning.

## UTC and Local Clocks

That happens because databases store moments as Coordinated Universal Time, the absolute global standard time scale, while servers convert them using local rules. Your app saves a timestamp, which is a specific recorded point on the timeline, into a column called a timestamp with time zone.

## The Wrong Offset

When a server in New York reads that raw entry without an explicit offset, it applies Eastern Standard Time instead of Greenwich. Every write operation must explicitly supply the offset, or the storage engine defaults to whatever local clock the machine happens to run on.

## Operational Check

When was the last time a user in a different country reported your app living in the wrong day entirely?
