# Integration note: Team5 (v1, go-live)

Copy this file, fill every angle bracket, and hand it to your paired Agentic AI
team. It is Part A of the cross-cohort runbook
(`../../../week-06-capstone/cross-cohort-runbook.md`); the full operating rules
for the window live there.

- **base_url** (client form, ends in `/v1` - paste into an OpenAI client):
  `https://t11.aidc.nadir.sh/v1`
- **service root** (no `/v1` - the runbook's triage curls and `verify.sh`
  build paths from this): `https://t11.aidc.nadir.sh`
- **model id:** `Qwen/Qwen2.5-1.5B-Instruct-AWQ`
- **auth:** bearer key, handed over 
- **modalities:** text in, text out, tool calls per the OpenAI schema.
- **example call:** 
  curl -s https://t11.aidc.nadir.sh/v1/chat/completions \
  -H "Authorization: Bearer $KEY" \
  -H 'Content-Type: application/json' \
  -d '{"model":"Qwen/Qwen2.5-1.5B-Instruct-AWQ","messages":[{"role":"user","content":"hello from outside"}]}'
- **SLOs we publish:** availability 99% over the window · TTFT p95 < 500 ms · error rate < 1%
- **limits, declared honestly:** max_tokens clamp 128 · concurrency knee ~16 · text-only serving
- **on-call:** Shahad Alkhattaf · Discord · response within 30 minutes during the window
