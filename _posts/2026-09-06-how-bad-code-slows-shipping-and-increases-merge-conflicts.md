---
layout: post
title: "How Bad Code Slows Shipping and Increases Merge Conflicts"
description: "Discover how unmanaged bad code in React projects leads to larger diffs, daily merge conflicts, and slower release cycles, and why a 30‑minute refactor can prevent weeks"
date: 2026-09-06
categories: [news]
---

Bad code doesn't just get ugly; it eventually stops your team from shipping.

When a module accumulates ad‑hoc fixes, the mental model erodes. New hires spend half their onboarding time tracing why a component renders twice instead of reading docs.

I saw this on a React app where a shared utility grew to 300 lines of conditional logic. The diff size jumped 40% and merge conflicts became daily. We slowed the release cadence from weekly to bi‑weekly. (I still have the commit in my history.)

The trade‑off is clear: spending time refactoring now saves weeks of firefighting later. The risk is over‑refactoring in the middle of a sprint; you can lock the team out of the next release.

This week, pick the largest file that hasn't been touched in a sprint and schedule a 30‑minute refactor session with its owner.

## Sources

- [https://zachkehs.com/blog/theres_no_limit_to_how_bad_code_can_get/](https://zachkehs.com/blog/theres_no_limit_to_how_bad_code_can_get/)
