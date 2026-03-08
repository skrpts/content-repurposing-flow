---
type: workflow
id: content-repurposing-flow
title: Content Repurposing Flow
description: "Transforms source content into multiple format adaptations per channel"
tags: [Tested]
connections:
  - target: content-repurposing
    type: uses
  - target: social-media-post-generator
    type: uses
  - target: newsletter-writer
    type: uses
metadata:
  estimated_duration: "5-15 minutes"
  trigger: manual
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
