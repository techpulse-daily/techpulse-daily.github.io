---
layout: post
title: "Why SQL LIMIT 10 Still Scans Millions of Rows"
description: "Learn why database queries with a LIMIT clause still read entire tables into memory, why it slows down your server, and how proper indexing fixes it."
date: 2026-11-02
categories: [evergreen]
youtube_id: X8jt8SBHeN0
---

A teacher grades one thousand essays just to hand back the ten best.

## Grading the whole stack

Your database does the exact same thing when you write limit ten without an index, which is a sorted map - a saved structure kept close by that tells the system where to look.

You ask for ten rows from your users table, but the query engine has no idea which rows match your sort order yet. So the disk reads every single million records into memory, sorting them all before it finally drops off the nine hundred ninety-nine thousand you never asked to see.

## Limit stops output, not work

The limit keyword stops the output, not the work, burning your server CPU just to throw away ninety-nine percent of the data it just fetched.

When was the last time a slow dashboard query made your browser freeze during a morning standup meeting? Check your query plans.
