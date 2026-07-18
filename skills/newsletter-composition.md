---
type: skill
id: newsletter-composition
title: Newsletter Writer
description: "Composing a complete newsletter edition from the selected content topics and updates"
tags: [Production, Content, Writing]
connections:
  - target: llm-service
    type: runs_on
metadata:
  estimated_duration: "4 minutes"
  avg_tokens: 3000
  trigger: manual
---

## Newsletter Writer

This skill composes a complete newsletter edition from the repurposed content and the selected topic ideas, producing a send-ready draft with a compelling subject line, engaging opening, structured sections, and a clear call to action.

### Core Capability

Given the content ideas surfaced earlier in the flow, this skill selects the main feature and quick-read items, then writes them up in a conversational yet professional voice matched to the audience profile.

### Method

1. **Topic selection:** From the supplied content ideas, choose the lead story and the supporting quick-read items that best fit the audience.
2. **Composition:** Draft the subject line, opening, structured sections, and sign-off with a call to action, keeping the tone consistent throughout.
3. **Coherence check:** Ensure the edition reads as a single cohesive piece rather than a list of disconnected fragments.

### Output Structure

A complete newsletter draft in markdown — subject line, opening, body sections, and closing call to action — ready for language polishing and review.
