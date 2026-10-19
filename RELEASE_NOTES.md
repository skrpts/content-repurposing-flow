# Release Notes

## v1.1.31
GH#1044 — the last of the required-but-undocumented inputs, resolved by testing whether the existing table name is itself required by a prompt rather than by how similar the names look. Renamed source_content to the name the prompt consumes; documented recent_content. Rows generated from the requiring prompt's own declared description, example and required flag. No behaviour change; documentation only.

## v1.1.30
GH#1044 — document the inputs this workflow's prompts REQUIRE but its Inputs table never listed. A user supplying exactly what the table asked for was running with required parameters unsatisfied — a silent wrong run, not a documentation nicety. Renamed 1 row(s) (source_content) to the name the prompt actually consumes; documented 7 input(s): audience_profile, campaign_topic, industry_news, key_messages, recent_content, target_platforms, upcoming_announcements. Every row is generated from the requiring prompt's own declared description, example and required flag — none invented. No behaviour change; documentation only.

## v1.1.29
GH#863 Wave 1 — fix K-045 intent/output mismatch. The `newsletter-writer` prompt (the promised newsletter deliverable) was never invoked by the workflow. Add a backing skill (`newsletter-composition`, title "Newsletter Writer") and wire it as the terminal content step after the platform guide, consuming the content ideas via an explicit `content_ideas` binding. Re-pin `polish-language`→1.0.6 and bind the output_step `source` ← the newsletter, so language-polish now polishes the real deliverable. +1 skill (total 3).

## v1.1.28
GH#845 — republish with American English (en-US) content, completing the source-only GH#805 flip that never reached the Hub. Copy only — no functional or behaviour change.

## v1.1.27
GH#745 — declare per-step `output: {name, type}` on every execution step (repurposed_content/text, ideas/list, brief/text, platform_guide/text, polished_content/text). Lights up the #744 rich flow-map with named, typed outputs. Content-only; no bindings or logic changes.

## v1.1.26
GH#645 Row 3 final — re-pin 5 prompt-deps to the new v1.0.2/v1.0.3 versions that now expose `nodes[].content` via /api/shared/<slug>/<v>/metadata (per GH#651 endpoint extension + d1Execute dual-mode fix). Engine validator's dep-aware loop-body `{{loop.item}}` interpolation check + binding from_step resolution now pass through deps for this consumer. No content changes; identity + dep-version repin only.

## v1.1.25
GH#645 Row 3b — migrate to K-037 dep-referenced schema. Strip 13 inline shared-content files and declare 13 hub-shared deps (UUID id + slug name + version + checksum from `gen-dep-checksums.mjs`). Closes pre-Step-3 inline-vendoring for this bundle.

## v1.1.24
Wave 2: re-signed with canonical engine signing pipeline.

## v1.1.23
Tags migrated inline into manifest (GH#586). tags.yaml retired.

## v1.1.22
Bundle re-signed with canonical engine signing pipeline (Wave 2 migration).

## v1.1.21
Signature fix — RELEASE_NOTES.md now included in integrity checksum.

## v1.1.20
Initial catalog release with full structural and content-quality validation. All scanner checks pass.
