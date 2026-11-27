# PeoplePilot — SimplAI HR Assistant Assignment

Author: **Vatsalya Roy**

PeoplePilot is an HR assistant built entirely on SimplAI for AsterByte Technologies (fictional). It supports:

1. Grounded HR policy Q&A (KB: `PeoplePilot_HR_Policy_v1`)
2. General resume evaluation with a score
3. Job description generation
4. JD-based candidate evaluation with a score
5. HR email drafting / approved sending (live in SimplAI; **email connector details are omitted from this repo**)

## Reviewer access

- Agent editor: https://app.simplai.ai/dashboard/agent/6b0828d5f178fc411b13424b?pageType=edit
- Published version: **1.0**
- Model: **openai/gpt-5.4**
- Assignment account login must be sent **privately to the reviewer** (never commit passwords)

Deployment integrations are disabled in this SimplAI workspace, so review is in-account.

## What’s in this repo

| Path | Contents |
|---|---|
| `configuration/` | Observed config + full Agent Profile |
| `policy/` | AsterByte HR policy used by the KB |
| `exports/` | Sanitized native agent export (no Send Email connector) |
| `evaluation/` | Model comparison results + live response extracts |
| `prompts/` | Non-email test prompts |
| `evidence/` | Sample trace screenshot |

## Model selection

Live Preview comparison on P01 / E01 / M04 / M05:

| Model | Result |
|---|---|
| openai/gpt-5 | 3/4 |
| **openai/gpt-5.4** | **4/4 (selected)** |
| anthropic/claude-sonnet-4-6 | 3/4 |
| openai/gpt-4o-mini | 3/4 |

Details: `evaluation/MODEL_COMPARISON_REPORT.txt` and `evaluation/model_runs/`.

## Architecture

User → SimplAI PeoplePilot agent → policy retrieval / structured generation → (for email) exact preview → user approval → Send Email action in SimplAI.

Business rules for scoring, citations, missing-evidence vs explicit mismatch, and email approval are enforced primarily by the Agent Profile.

## Limitations

- Full 29-case matrix is not claimed as fully executed; comparison used a shared critical subset.
- Email connector configuration is intentionally not packaged here.
- Import portability of the export was not tested.
