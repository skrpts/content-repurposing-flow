---
type: workflow
id: content-repurposing-flow
title: Content Repurposing Flow
description: "Transforms source content into multiple format adaptations per channel"
tags: [Tested, Content, Writing]
connections:
  - target: content-repurposing
    type: uses
  - target: content-ideation
    type: uses
  - target: content-briefing
    type: uses
  - target: llm-service
    type: runs_on
  - target: headline-writing
    type: references
  - target: social-media-platform-guide
    type: uses
  - target: language-polish
    type: uses
metadata:
  estimated_duration: "5-15 minutes"
  trigger: manual
output_step: "social-media-platform-guide"
composite_steps:
  - "content-repurposing"
  - "content-ideation"
  - "content-briefing"
  - "social-media-platform-guide"
  - "language-polish"
execution:
  - skill: "content-repurposing"
    prompt: "social-media-post-generator"
    step_type: "generation"
  - skill: "content-ideation"
    prompt: "generate-content-ideas"
    step_type: "generation"
    context:
      content_context: ""
  - skill: "content-briefing"
    prompt: "create-content-brief"
    step_type: "generation"
    context:
      target_audience: ""
  - skill: "social-media-platform-guide"
    step_type: "generation"
  - skill: "language-polish"
    prompt: "polish-language"
    step_type: "content"
---

## Overview

This workflow takes a single piece of source content and produces multiple format adaptations tailored to different channels. It maximises the ROI on content creation by systematically repurposing material for social media, email, and other platforms.

## Pipeline Stages

### Stage 1: Content Adaptation

**Input:** Source content (blog post, article, video transcript, podcast notes, etc.)

Invoke the **content-repurposing** skill to analyse and transform the source content into multiple platform-specific formats. Identify core messages, supporting data points, and segments that map well to each target format.

**Output:** Adapted content per target format.

### Stage 2: Social Media Posts

**Input:** Adapted content from Stage 1

Invoke the **social-media-post-generator** prompt to create platform-specific posts for LinkedIn, X/Twitter, Instagram, and Threads. Respect each platform's character limits, hashtag conventions, and native tone.

**Output:** Ready-to-publish social media posts per platform.

### Stage 3: Newsletter Edition

**Input:** Adapted content from Stage 1

Invoke the **newsletter-writer** prompt to compose a newsletter edition from the repurposed content. Include a compelling subject line, engaging opening, structured sections, and a call to action.

**Output:** Complete newsletter draft ready for review.

## Inputs

| Name | Required | Description | Example |
|------|----------|-------------|---------|
| `{{input.source_content}}` | Yes | Source content | `Paste the relevant brief, notes, source material, or dataset here.` |
| `{{input.brand_voice}}` | No | Brand voice guidelines | `Professional but approachable. Avoid jargon. Use active voice.` |

## Outputs

| Name | Description |
|------|-------------|
| Adapted content per target format | Adapted content per target format |
| Ready-to-publish social media posts per platform | Ready-to-publish social media posts per platform |
| Complete newsletter draft ready for review | Complete newsletter draft ready for review |

## Setup

Before running this workflow:

1. No external services required — paste your content directly and provide any supporting context as inputs or source nodes.
2. Review the included documents, assets, or source nodes and customise them to match your team, brand, or domain conventions where needed.
3. No specific AI provider or API key is required beyond your configured skrptiq LLM provider.

## Provider Notes

- Most stages work with any capable model; stronger models usually improve synthesis, judgement, and writing quality.
- Extraction, classification, and formatting steps generally run well on smaller or faster models.
- Because there are no vendor-specific integrations here, provider choice is mostly a trade-off between speed, quality, and cost.

## Example Input

To test this workflow immediately after import:

```
Source Content: "Paste the relevant brief, notes, source material, or dataset here."
Brand Voice: "Professional but approachable. Avoid jargon. Use active voice."
```
