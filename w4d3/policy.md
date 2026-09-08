# Resource Policy

Policy: Serving is guaranteed enough resources to protect its p95 SLO. Batch can use idle CPU but throttles first when resources are needed. Dashboard stays small but can burst during heavy refreshes.

## Serving

```yaml
resources:
  requests:
    cpu: "2"
    memory: 1Gi
  limits:
    cpu: "2"
    memory: 1Gi
```

## Batch

```yaml
resources:
  requests:
    cpu: 250m
    memory: 256Mi
  limits:
    cpu: 500m
    memory: 512Mi
```

## Dashboard

```yaml
resources:
  requests:
    cpu: 250m
    memory: 256Mi
  limits:
    cpu: "1"
    memory: 512Mi
```

## Defense

Batch throttles first because it has no immediate deadline, while serving must protect its p95 SLO. Limiting the noisy neighbour kept serving latency stable and slightly improved p95 from 4 ms to 3 ms.

## Step 4 Evidence

### Unlimited burners
LATENCY n=571 fails=0 p50=2ms p95=4ms

### Limited burners (CPU limit: 500m)
LATENCY n=574 fails=0 p50=2ms p95=3ms

Result: The CPU-limited noisy neighbour kept serving latency stable, with p95 changing from 4 ms to 3 ms.
