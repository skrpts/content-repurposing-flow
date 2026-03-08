---
type: prompt
id: social-media-post-generator
title: Social Media Post Generator
description: "Creates platform-specific social media posts"
tags: []
connections: []
metadata:
  output_format: markdown
  prompt_type: task
---

## Purpose

Generates ready-to-publish social media posts tailored to each platform's format, tone, and constraints.

## Prompt

You are a social media copywriter. Create posts for the specified platforms based on the content below. For each platform, respect character limits, include relevant hashtags, and match the platform's native tone.

## Source Content
{{content}}

## Platforms
{{platforms}}

## Brand Voice
{{brand_voice}}

## Call to Action
{{cta}}
