# Integration note: team 11 (v1, go-live)

Copy this file, fill every angle bracket, and hand it to your paired Agentic AI
team. It is Part A of the cross-cohort runbook
(`../../../week-06-capstone/cross-cohort-runbook.md`); the full operating rules
for the window live there.

- **base_url** (client form, ends in `/v1` - paste into an OpenAI client):
  `https://t11.aidc.nadir.sh/v1`
- **service root** (no `/v1` - the runbook's triage curls and `verify.sh`
  build paths from this): `https://t11.aidc.nadir.sh`
- **model id:** `Qwen/Qwen2.5-1.5B-Instruct-AWQ`
- **auth:** bearer key, handed over in person
- **modalities:** text in, text out, tool calls per the OpenAI schema.
- **example call:** `curl -s https://t11.aidc.nadir.sh/v1/models -H "Authorization: Bearer REDACTED"`
- **SLOs we publish:** availability 95% over the window · TTFT p95 under 200 ms (tier 1) · error rate under 5%
- **limits, declared honestly:** max_tokens clamp 1024 · concurrency knee 4
- **on-call:** Rasheed Alsubaie · Discord · response within 15 minutes during the window
