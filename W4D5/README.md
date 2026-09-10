# Lab W4D5: Go-Live (Team 5)

## Predictions
1. Non-Kubernetes points of failure: The application pod crashing, and the named tunnel (Cloudflare) going offline.
2. First client request on startup: `GET /v1/models` (to verify the available model before sending a completion request).
3. Honest SLO measurement: For Tier 1, we publish TTFT p95, measured from outside the cluster (consumer's perspective).

## Verification

<img width="893" height="49" alt="Screenshot 2026-09-10 223814" src="https://github.com/user-attachments/assets/9deee6df-455a-46f2-8ae3-4c2f2a5be3a8" />
