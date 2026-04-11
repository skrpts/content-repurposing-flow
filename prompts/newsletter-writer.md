---
type: prompt
id: newsletter-writer
title: Newsletter Writer
description: "Composes a newsletter edition from curated topics and updates"
tags: [Production, Content, Writing]
inputs:
  audience_profile:
    label: "Audience Profile"
    description: "Profile of the target audience"
    example: "Marketing managers, 30-45, at companies with 50-500 employees"
    required: true
    type: text
  recent_content:
    label: "Recent Content"
    description: "Content published recently"
    example: "Last 5 blog posts with titles, dates, and performance metrics"
    required: true
    type: text
  upcoming_announcements:
    label: "Upcoming Announcements"
    description: "Planned announcements or releases"
    example: "New pricing tier launching May 15. Partnership announcement June 1."
    required: true
    type: text
  industry_news:
    label: "Industry News"
    description: "Recent industry news or trends relevant to the analysis"
    example: "OpenAI launched GPT-5. Notion added AI blocks."
    required: true
    type: text
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

{{steps.Content Ideation.output}}

Using the selected topics above, write the newsletter edition covering the main feature and quick-read items.

## Tone

Conversational yet professional — match the audience profile and brand expectations.
