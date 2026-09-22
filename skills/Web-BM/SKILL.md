---
name: Web-BM
description: Use to design a web service's business model (BM) concretely — choice of revenue source, pricing policy, conversion funnel, key metrics. Use for requests like "design a BM", "I don't know what price to set" ("BM 짜줘", "가격을 얼마로 해야할지 모르겠어"). Continues mid-Web-Plan whenever BM needs to go deeper.
---

# Web-BM

For when the service's concept and target are already roughly settled, and the question is "so how does this actually make money" — turns that into a concrete design.

**Write the output in the language the user is using with you (Korean by default).** These instructions are in English only for maintainability; it's not a cue to answer in English.

## 1. Confirm the premise first

If concept/target aren't settled yet, point the user to Web-Plan first. BM can't be designed in a vacuum — you need to know who's being sold what before designing how.

Confirm (skip anything already covered in conversation):
- What is the target user spending money on right now for this same problem (the cost of the existing alternative anchors the price)
- What BM do similar services use — if unknown, suggest Web-DeepSearch research

## 2. Compare and recommend models

Using the model table in `../references/bm-web.md` (skip re-reading if already read this conversation), pick 2-3 candidates that fit this service and briefly evaluate the pros/cons of each in this service's context. Don't present just one — compare, then state the reasoning for the recommendation. Combining several models is often the better answer (e.g. freemium + ads).

## 3. Design the price and conversion points

- Propose concrete price candidates as numbers (with reasoning, not a vague "something reasonable")
- If there's a free tier, define the concrete trigger that drives upgrade (usage cap, advanced feature, team feature, etc.)
- Identify where in the user flow the payment/upgrade prompt appears naturally — is it a hard wall, or value-first-then-prompt?

## 4. Define metrics

Full financial modeling isn't needed, but state at least a direction for: conversion target, 1-2 core revenue metrics to track (MRR, ARPU, etc.), and a rough break-even sense (how many paying users, at least in order of magnitude).

Format the result so it can drop straight into the BM section of an existing plan, if one exists.
