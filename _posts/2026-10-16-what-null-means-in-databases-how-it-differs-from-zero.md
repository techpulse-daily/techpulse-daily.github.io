---
layout: post
title: "What NULL Means in Databases: How It Differs From Zero"
description: "Learn what NULL actually means in database design and how this missing value marker behaves differently than zero or blank strings during queries and joins."
date: 2026-10-16
categories: [evergreen]
---

An empty box sits on the form, untouched.

That empty box on the form is exactly what databases store as NULL, a special marker that says no value was ever entered, not even an empty string. NULL differs from zero, which is a real numeric value meaning 'nothing' in counting, and also differs from a blank string, which is simply an empty piece of text.

## How NULL Behaves in Queries

When you ask the database to add up a column, it skips any row that holds NULL because adding an unknown would corrupt the total.

During a join, the engine compares fields; if one side contains NULL the comparison fails, so the combined row is omitted, and any later calculations receive fewer inputs.

## Troubleshooting Missing Data

Recall a dashboard that showed a flat line—could a hidden NULL be the reason the numbers never appeared?
