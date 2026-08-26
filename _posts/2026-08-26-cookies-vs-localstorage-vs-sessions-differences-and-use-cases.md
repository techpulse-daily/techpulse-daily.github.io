---
layout: post
title: "Cookies vs localStorage vs Sessions: differences and use cases"
description: "Learn the key differences between cookies, localStorage, and server sessions, including how they store data, persistence, and ideal scenarios for each."
date: 2026-08-26
categories: [evergreen]
---

Your phone’s three pocket memories: a sticky note, a zip‑locked pouch, and a day‑long diary. Websites use three similar spots to remember who you are. A cookie — a tiny text file stored by the browser that the server reads on each request — is like the sticky note you keep on your fridge; it travels with every page load and can expire after days or weeks. localStorage — a key‑value store that lives in the browser and never sends data to the server automatically — works like a zip‑locked pouch in your back pocket; it stays until you or the site explicitly clears it, persisting across sessions. A session — the server‑side record that lives only while your browser tab stays open — is like a day‑long diary you write in; once you close the tab, the entry disappears. Cookies are sent on every request, so they’re good for authentication but add overhead. localStorage holds larger amounts, perfect for UI preferences, but can’t be read by the server directly. Sessions keep sensitive data safe on the server, but they vanish when you leave. Now you understand why a site might choose a sticky‑note cookie, a zip‑locked localStorage, or a day‑long session to recognize you.

When have you needed to switch from using a cookie to localStorage to solve a UI persistence issue?

## Pocket Memories: Sticky Note, Pouch, Diary

Three ways browsers keep track of you, like everyday items in your pockets.

## Cookie = Sticky Note on the Fridge

Small text file sent with each request; expires after a set time.

## localStorage = Zip‑Locked Pouch

Key‑value store in the browser; persists until cleared, not sent to server.

## Session = Day‑Long Diary

Server‑side record that lives only while the tab stays open.

## Why Choose One Over Another?

Cookies add request weight, localStorage holds more data, sessions protect sensitive info.
