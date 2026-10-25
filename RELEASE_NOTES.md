# Release Notes

## v1.1.33
GH#1124 — bind the source content for step 1, which has been hard-erroring on every run.

Step 1 invokes `social-media-post-generator`, whose body read `{{steps.Content Briefing.output}}` — a step at position **3**. A forward reference: this workflow declares no `requires` edges and `DeriveOrderingEdges` defaults to false, so nothing reorders the steps, the reference never resolves, and the step hard-errors. **Step 1 could not complete, on any run.**

The prompt now declares a required `source` slot (1.0.5), and this workflow binds it to `{{input.recent_content}}` — the content this flow exists to repurpose, and the input its own table marks required as *"Content published recently"*.

**Bound from an input rather than from a step, deliberately.** At position 1 there is no earlier step to bind, and reordering the workflow to manufacture one would change published behaviour to satisfy a mechanism. The prompt's own description — *"Creates platform-specific social media posts from source content"* — is satisfied by the flow's source content, not by a brief produced two steps later.

`recent_content` is now also DECLARED on this workflow node, mirroring the declaration `prompts/newsletter-writer.md` already carried. The Inputs table documented it but a table is not a declaration, and binding it surfaced that — the canonical scan refused `from_input: "recent_content"` until the node declared it.

## v1.1.32
GH#1100 consumer wave (batch 3) — declare the data flow this workflow was resolving positionally.

Each stage below now receives its input through a declared `bindings:` entry instead of `default_from_previous`, which K-073 revoked. **The value is unchanged**: every binding names the step that immediately precedes it, which is exactly what the positional default resolved to. What changes is that the dependency is stated rather than inferred from position, so a reorder can no longer silently feed a stage the wrong artefact.

Bindings added:
  `create-content-brief` ← `from_step: "Content Ideation"` (step 3)

Dependency pins moved to the published versions that declare these slots:
  `create-content-brief` 1.0.4 → 1.0.5
  `generate-content-ideas` 1.0.2 → 1.0.3
  `polish-language` 1.0.6 → 1.0.7
  `social-media-platform-guide` 1.0.1 → 1.0.2
  `social-media-post-generator` 1.0.3 → 1.0.4
  `write-headlines` 1.0.3 → 1.0.7

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
