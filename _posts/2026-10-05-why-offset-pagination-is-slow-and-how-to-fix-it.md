---
layout: post
title: "Why Offset Pagination is Slow and How to Fix It"
description: "Learn why high page numbers crush database performance with offset pagination and how cursor-based pagination eliminates wasted CPU cycles at scale."
date: 2026-10-05
categories: [evergreen]
youtube_id: yFhgM-192hA
---

Asking a librarian for book fifty thousand by making them count from book number one is how your app loads page five thousand.

## How offset pagination works

This pattern is called offset pagination, where a database — an organized store for your app data — skips rows by walking every single one from the very beginning.

When a user asks for page five thousand with a page size of twenty, the database engine must fetch one hundred thousand rows, discard ninety-nine thousand, and keep just the last twenty.

## The performance cost

As your table grows to millions of records, that walk turns into seconds of waiting, burning CPU cycles just to throw away data.

## The alternative: cursor pagination

Instead, remember the last seen ID and fetch only what comes after it.

How many queries in your current production database are still using offset pagination right now?
