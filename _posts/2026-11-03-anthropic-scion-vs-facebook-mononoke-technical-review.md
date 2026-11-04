---
layout: post
title: "Anthropic Scion vs Facebook Mononoke: Technical Review"
description: "An external engineer analyzes Anthropic's Scion migration, compares its design and workflow to Facebook's Mononoke, and explains scalability benefits for massive monorepo"
date: 2026-11-03
categories: [news]
---

Anthropic published a blog post detailing its new centralized version control system, Scion, and its migration from Git. An engineer on the Source Control team at Databricks subsequently published an outsider's technical commentary on the design, development process, and similarities to Facebook's Mononoke.

## Why it matters

Managing massive monorepos requires moving away from Git-style trees toward changesets, optional and sparse working copies, and content-addressed object storage that enables horizontal scalability. These architectural shifts highlight how modern large-scale development environments handle performance bottlenecks, push contention, and code navigation at scale.

## The key fact

Anthropic fully migrated its monorepo from Git to Scion in five months using a team of 7 people and an undisclosed number of Claude tokens.

## Context

Major tech companies dealing with massive monorepos—such as Facebook, Google, and Anthropic—have increasingly turned to custom internal version control systems like Mononoke, Sapling, and Scion to overcome the scalability limitations of Git.

## Sources

- [https://typesanitizer.com/blog/scion.html](https://typesanitizer.com/blog/scion.html)
