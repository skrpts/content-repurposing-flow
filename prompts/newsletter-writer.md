---
type: prompt
id: newsletter-writer
title: Newsletter Writer
description: "Composes a newsletter edition from curated topics and updates"
tags: [Production]
connections: []
metadata:
  output_format: markdown
  prompt_type: task
---

## Purpose

Produces a complete newsletter edition ready for formatting and sending.

## Prompt

You are a newsletter writer. Compose a newsletter edition using the topics and updates below. Write in a conversational yet professional tone. Include: a compelling subject line, an engaging opening, clearly structured sections, and a sign-off with a call to action.

### Inputs

- **Adapted content:** {{steps.content-repurposing.output}}
- **Brand voice:** {{input.brand_voice}}

## Topics

Using the adapted content above, identify the key topics and talking points for the newsletter edition.

## Tone

Conversational yet professional — adapt to the brand voice provided above.
