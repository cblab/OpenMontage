---
name: luma-uni-image
description: |
  Generate or edit still images with the Luma Agents uni-1 / uni-1-max models through the `luma_uni_image` tool. Use when: (1) a high-value hero frame or key visual is needed, (2) an image must follow up to 9 reference images, (3) an existing image should be edited with a text instruction. Requires LUMA_AGENTS_API_KEY.
allowed-tools: Bash, Read, Write
metadata:
  openclaw:
    requires:
      env_any:
        - LUMA_AGENTS_API_KEY
---

# Luma uni-1 image generation and editing

The `luma_uni_image` tool (provider `luma_agents`, API `https://agents.lumalabs.ai/v1`) wraps the Luma Agents image models `uni-1` (default) and `uni-1-max`. Jobs are asynchronous and paid. The tool is marked beta.

## When to use it

- High-value hero frames and reference-guided compositions.
- Controlled edits of an existing image (`operation: "edit"`).
- Not for bulk, inexpensive plates when FLUX is sufficient.

## Inputs

| Field | Meaning |
|---|---|
| `prompt` | Required, 1–6000 characters. |
| `operation` | `generate` (default) or `edit`. |
| `model` | `uni-1` (default) or `uni-1-max`. |
| `aspect_ratio` | Default `16:9`. |
| `output_format` | `png` (default) or `jpeg`. |
| `source_path` / `source_url` | Source image for `edit`. A local file must be at most 30 MB; a URL must use HTTPS. |
| `reference_paths` / `reference_urls` | Up to 9 reference images each, same limits. |
| `output_path` | Where to save the result. |
| `timeout_seconds` | Default 600. |

## Setup

Set `LUMA_AGENTS_API_KEY` (the tool also accepts `LUMA_API_KEY`). Without a key the tool reports itself as unavailable.

## Verification

Open the saved image and the provenance metadata the tool writes next to it before using the result.
