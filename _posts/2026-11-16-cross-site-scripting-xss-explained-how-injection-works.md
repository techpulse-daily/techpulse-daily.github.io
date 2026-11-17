---
layout: post
title: "Cross-Site Scripting (XSS) Explained: How Injection Works"
description: "Learn how cross-site scripting vulnerabilities allow attackers to inject malicious code into web pages and how input sanitization stops session hijacking."
date: 2026-11-16
categories: [evergreen]
---

A stranger slips a hidden note into a public guestbook, and every reader later steals their cash.

## How Injection Works

That trick is called Cross-Site Scripting, where an attacker injects malicious code, a tiny program, into a page that every visitor's browser runs. When the page renders, the browser treats the injected script like any other script tag, executing it with the same privileges as the site's own code. That script can read cookies, which are small data pieces that keep you logged in, and send them to the attacker, letting them hijack your session.

## The Request Path and the Fix

The request travels in a specific path: a user writes a note, the server saves the raw text, the page returns that text inside the HTML, and the browser runs it. The fix is to sanitize, meaning to clean every piece of input, converting characters like < and > into harmless symbols before storing them.

## Checking Your Account

Have you ever posted a comment and later noticed strange activity on your account?
