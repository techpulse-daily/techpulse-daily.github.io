---
layout: post
title: "Claude: blue Add to Cart button slowed checkout load"
description: "We changed the Add to Cart button color to brand‑blue in Claude, which triggered a 350 KB CSS bundle reload and increased first‑paint time from 1.2 s to 2.0 s on 4G."
date: 2026-09-10
categories: [news]
---

Changing a button’s hue shouldn’t be a performance story, but it became one for us.
We shipped a tiny CSS tweak – flipping the “Add to Cart” button from gray to brand‑blue – and the next sprint the checkout page’s first‑paint time jumped from 1.2 s to 2.0 s on a typical 4G handset. The diff was a single line: `background:#0055ff;` added to the global `.btn` rule. It pulled in the entire design system’s dark‑theme stylesheet because the selector specificity forced the compiler to re‑bundle a 350 KB CSS chunk that had been lazy‑loaded elsewhere.
The root cause was pure deadline pressure. The product manager wanted the color change overnight, and we bypassed the usual CSS‑module audit. The build system treated the new rule as a global import, invalidating the previously split bundle. No one noticed because our local dev server always served the full CSS anyway.
Banning global CSS changes outright feels like swapping one risk for another – you end up with inline styles everywhere, bloating HTML and making future theming impossible. (I once tried that and spent three days untangling a component that suddenly stopped rendering on Safari.)
If you’re curious, open Chrome DevTools, go to the Network tab, filter by “css”, and sort by size. You’ll see the new 350 KB file appears on every page load. Spend ten minutes deleting that entry from the build and measuring the paint time again – you’ll likely shave off a few hundred milliseconds without any ticket.

## Sources

- [https://opusfived.dev/](https://opusfived.dev/)
