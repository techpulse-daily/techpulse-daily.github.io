---
layout: post
title: "Soft Deletes Pattern: Database Design and Unique Index Fixes"
description: "Learn how database soft deletes work using a deleted_at timestamp column and how to handle unique index conflicts with hidden records."
date: 2026-10-03
categories: [evergreen]
youtube_id: I-x19rebxeo
---

Dragging files straight to the recycling bin instead of shredding them is the only reason the undo button works.

Databases use this exact trick called soft deletes, a saved state where rows are marked hidden instead of being erased. Instead of executing a permanent delete command, the system updates a single column called deleted_at with a timestamp. Every regular query gets an extra filter tacked on automatically to hide any row that has a timestamp in that column.

## Operational Recovery

When a customer calls support demanding their deleted account back, recovery takes one second instead of a messy backup restore.

## Index Conflicts

The catch is that unique indexes break if two users create accounts with the same email, because the old hidden row still takes up space.

How does your main user table handle unique emails when an account is sitting in the deleted state?
