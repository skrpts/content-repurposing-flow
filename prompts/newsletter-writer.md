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

- **Audience profile:** {{input.audience_profile}}
- **Recent content:** {{input.recent_content}}
- **Upcoming announcements:** {{input.upcoming_announcements}}
- **Industry news:** {{input.industry_news}}

## Topics

{{steps.content-ideation.output}}

Using the selected topics above, write the newsletter edition covering the main feature and quick-read items.

## Tone

Conversational yet professional — match the audience profile and brand expectations.
