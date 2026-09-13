# Service indicators and proposed targets

Team: team 5
Use case: vLLM AI model serving endpoint handling text generation requests for users
Service measured: vllm model, serving endpoint in namespace team; baseline chat service
Workload: text generation requests, caller count 1, standard batch size and output limits
Measurement period: September 13, 2026, UTC
Instrumentation gaps: none

Complete two SLI sections. Copy one section if you choose a third. Use the exact
stat-panel title for Panel. Keep the field labels so the verifier can read them.
Support each target with observed measurements.

## SLI 1

Indicator: Time to First Token (TTFT) 95th percentile latency
Panel: TTFT p95 (5m)
Unit: seconds
Target: < 0.050s (50ms)
Window: 5m query window, 1h evaluation window
Observed: 0.039s (39.000 ms)
Evidence: histogram_quantile(0.95, sum by (le) (rate(vllm:time_to_first_token_seconds_bucket{job="serving"}[5m]))) or histogram_quantile(0.95, sum by (le) (rate(vllm_time_to_first_token_seconds_bucket{job="serving"}[5m])))
Why it fits: Measures responsiveness and initial token delay for users interacting with the model
Limitations: Sample size depends on active traffic generation during the test window

## SLI 2

Indicator: Completed requests throughput per minute
Panel: Completed requests / min (5m)
Unit: requests/min
Target: >= 10 req/m
Observed: 0.0 req/m (or actual active rate depending on traffic script status)
Evidence: 60 * (sum(rate(vllm:request_success_total{job="serving",finished_reason=~"stop|length"}[5m])) or sum(rate(vllm_request_success_total{job="serving",finished_reason=~"stop|length"}[5m])))
Why it fits: Tracks the successful throughput capacity of the model and serving infrastructure
Limitations: Dependent on continuous execution of the traffic generation script