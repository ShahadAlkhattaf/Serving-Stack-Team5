# Service report

Team: Team 5
Use case: HR AI (serving baseline only; HR workflow not evaluated in this lab)
Service and model: team-serving — Qwen/Qwen2.5-1.5B-Instruct-AWQ.
Measured requests or tasks: 120 artificial chat completion requests.
Indicator and unit: p95 Time to First Token (TTFT), seconds
SLO target and window: p95 TTFT < 0.1 seconds over a 5-minute window
Measurement start and end: 2026-09-14T08:46:37Z to 2026-09-14T08:49:37Z
Workload: Artificial chat traffic through NodePort 30800 using the team API key, with up to four concurrent callers and max_tokens=64.
Observed result and sample count: p95 TTFT = 0.0389 seconds over 120 requests.
Evidence: Grafana/Prometheus TTFT p95 measurement using the vLLM time-to-first-token histogram, with notification evidence saved in `notification-evidence.jsonl`.
Conclusion: met
Limitations: This result is based on a short artificial workload and does not establish compliance over a longer production period. The workload may not represent sustained production traffic, and TTFT does not measure model-output quality.
Follow-up action: Repeat the measurement over a longer period with representative production-like traffic and concurrency.

## Measurement query

```promql
histogram_quantile(
  0.95,
  sum by (le) (
    rate(
      vllm:time_to_first_token_seconds_bucket{
        job="serving",
        model_name="Qwen/Qwen2.5-1.5B-Instruct-AWQ"
      }[5m]
    )
  )
)
```
Evaluation: Instant query using a fixed 5-minute rate window.

The measurement is taken from Prometheus metrics exported by the `team-serving` vLLM service and filtered to the serving job and deployed model. It measures p95 time to first token and does not measure total response latency or model-output quality.

## Service alert

Condition and unit:  p95 TTFT > 0.1 seconds
Evaluation interval: 1 minute
Pending period: 2 minutes
Relationship to the SLO: The alert detects a breach of the documented p95 TTFT target of < 0.1 seconds. The pending period requires the breach to persist across successive evaluations.
First response to a notification: Check the `team-serving` service and recent request latency to determine whether the latency increase is persistent.

## Notification test

Firing received at: 2026-09-14T08:38:55Z
Resolved received at: 2026-09-14T08:39:51Z
What the test establishes: The artificial `Lab notification test` successfully fired and resolved, and Grafana delivered both notifications to the `Lab inbox` webhook receiver. This verifies notification delivery and recovery handling, not recovery of the model service.
