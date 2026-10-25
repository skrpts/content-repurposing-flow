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
  - target: newsletter-composition
    type: uses
  - target: language-polish
    type: uses
inputs:
  recent_content:
    label: "Recent Content"
    description: "Content published recently"
    example: "Last 5 blog posts with titles, dates, and performance metrics"
    required: true
    type: text
metadata:
  estimated_duration: "5-15 minutes"
  trigger: manual
output_step: "language-polish"
composite_steps:
  - "content-repurposing"
  - "content-ideation"
  - "content-briefing"
  - "social-media-platform-guide"
  - "newsletter-composition"
  - "language-polish"
execution:
  - skill: "content-repurposing"
    prompt: "social-media-post-generator"
    step_type: "generation"
    output: { name: "repurposed_content", type: "text" }
    bindings:
      source:
        from_input: "recent_content"
  - skill: "content-ideation"
    prompt: "generate-content-ideas"
    step_type: "generation"
    output: { name: "ideas", type: "list" }
    context:
      content_context: "No additional context"
    bindings:
      source_content:
        from_step: "Content Repurposing"
        field: output
  - skill: "content-briefing"
    prompt: "create-content-brief"
    step_type: "generation"
    output: { name: "brief", type: "text" }
    context:
      target_audience: "General professional audience"
    bindings:
      source:
        from_step: "Content Ideation"
        field: output
  - id: "social-media-platform-guide"
    step_type: "local.template"
    output: { name: "platform_guide", type: "text" }
  - skill: "newsletter-composition"
    prompt: "newsletter-writer"
    step_type: "generation"
    output: { name: "newsletter", type: "text" }
    bindings:
      content_ideas:
        from_step: "Content Ideation"
        field: output
  - skill: "language-polish"
    prompt: "polish-language"
    step_type: "content"
    output: { name: "polished_content", type: "text" }
    context:
      voice_profile: "Neutral professional tone"
      grammar_strictness: "Professional"
    bindings:
      source:
        from_step: "Newsletter Writer"
        field: output
---

## Overview

This workflow takes a single piece of source content and produces multiple format adaptations tailored to different channels. It maximizes the ROI on content creation by systematically repurposing material for social media, email, and other platforms.

## Pipeline Stages

### Stage 1: Content Adaptation

**Input:** Source content (blog post, article, video transcript, podcast notes, etc.)

Invoke the **content-repurposing** skill to analyze and transform the source content into multiple platform-specific formats. Identify core messages, supporting data points, and segments that map well to each target format.

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
| `{{input.recent_content}}` | Yes | Content published recently | `Last 5 blog posts with titles, dates, and performance metrics` |
| `{{input.brand_voice}}` | No | Brand voice guidelines | `Professional but approachable. Avoid jargon. Use active voice.` |
| `{{input.audience_profile}}` | Yes | Profile of the target audience | `Marketing managers, 30-45, at companies with 50-500 employees` |
| `{{input.campaign_topic}}` | Yes | The topic or theme for the campaign | `Product launch for new AI features` |
| `{{input.industry_news}}` | Yes | Recent industry news or trends relevant to the analysis | `OpenAI launched GPT-5. Notion added AI blocks.` |
| `{{input.key_messages}}` | Yes | Core messages to communicate | `Save 10 hours/week on repetitive AI tasks. No code required.` |
| `{{input.target_platforms}}` | Yes | Platforms to create content for | `LinkedIn, Twitter` |
| `{{input.upcoming_announcements}}` | Yes | Planned announcements or releases | `New pricing tier launching May 15. Partnership announcement June 1.` |

## Outputs

| Name | Description |
|------|-------------|
| Adapted content per target format | Adapted content per target format |
| Ready-to-publish social media posts per platform | Ready-to-publish social media posts per platform |
| Complete newsletter draft ready for review | Complete newsletter draft ready for review |

## Setup

Before running this workflow:

1. No external services required — paste your content directly and provide any supporting context as inputs or source nodes.
2. Review the included documents, assets, or source nodes and customize them to match your team, brand, or domain conventions where needed.
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
