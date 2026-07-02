# Release Notes

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
Initial catalogue release with full structural and content-quality validation. All scanner checks pass.
