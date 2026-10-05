---
layout: post
title: "Git Post-Checkout Hook Attack Targets Developers"
description: "Learn how attackers use malicious Git post-checkout hooks in shared repositories to execute arbitrary code and compromise developer credentials."
date: 2026-10-05
categories: [news]
---

Frank Wiles was targeted by an attacker posing as an Ed Tech client who shared a Dropbox folder containing a hidden .git directory. When asked to switch to an 'NDA branch' to sign an agreement, Wiles discovered a malicious post-checkout hook designed to execute arbitrary code.

## Why it matters

The attack uses standard Git workflows that developers rely on daily, making it easy for unsuspecting programmers to accidentally execute malicious code simply by switching branches. The post-checkout hook utilized a Vercel app for command and control to download, execute, and delete an operating system-specific binary.

## The key fact

The malicious post-checkout hook was configured to use a Vercel app for command and control to download an OS specific binary, make it executable, run it, and then delete itself.

## Context

Attackers are increasingly using fake project inquiries and shared repositories containing malicious Git hooks to target developers in attempts to gain unauthorized access to accounts and client infrastructure.

## Sources

- [https://frankwiles.com/posts/i-got-targeted/](https://frankwiles.com/posts/i-got-targeted/)
