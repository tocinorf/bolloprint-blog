---
slug: whats-new-v0-14-a-url-for-every-language
title: "What's new in v0.14: every language now has its own address"
description: BolloPrint.com spoke six languages but Google only saw one. That's fixed — and it unlocked 174 pages of the user manual along the way.
version: v0.14
date: 2026-09-04
updated: 2026-09-04
tags: [news]
draft: true
---

Until this release, `bolloprint.com/pricing` served all six languages at **the
same address**: the server looked at your browser's language and gave you yours.
That works fine for a person. For a search engine, it doesn't.

Google crawls without a preferred language, so it always received the English
version — and that was the only one it indexed. The other five weren't ranking
badly: they **didn't exist** as far as search was concerned, because there was no
URL to point at.

## What changes

Every language gets its own address. English stays exactly where it was — so no
existing URL changes — and the other five carry the language in the path:

- `bolloprint.com/pricing` — English
- `bolloprint.com/es/pricing` — Spanish
- `bolloprint.com/fr/pricing` — French

And so on for all six. They declare each other as translations, so they don't
compete: search engines understand they're the same page in another language and
show each visitor the right one.

:::info
Share a link now and it arrives in the language you saw it in. Before, everyone
opened it in their own — which wasn't always the one you meant to show them.
:::

## The biggest win

The user manual is 29 documents translated into six languages — **174 pages** —
that until now were indexed as 29, in English. That content was already written
and translated; it just had nowhere to live.

## And one thing that doesn't change

Sign-in and account pages behave exactly as before, detecting your language the
way they always did. They aren't indexed, so they never needed an address of
their own: less surface touched, less that can break.
