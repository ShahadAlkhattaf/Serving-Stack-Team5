**Policy:**
`serving` is guaranteed, `dashboard` bursts during spikes, and `batch` is the first to throttle.

**Resources:**

* serving (Guaranteed):
```yaml
resources:
  requests:
    cpu: "2"
    memory: "2Gi"
  limits:
    cpu: "2"
    memory: "2Gi"

dashboard (Burstable):

YAML
resources:
  requests:
    cpu: "100m"
    memory: "128Mi"
  limits:
    cpu: "1"
    memory: "512Mi"

batch (Throttled):

YAML
resources:
  requests:
    cpu: "50m"
    memory: "128Mi"
  limits:
    cpu: "500m"
    memory: "256Mi"

Defense:
Throttling batch is justified because our tests proved that an unbounded neighbor degraded the serving p95 latency to 5000ms (all requests failed), whereas a throttled neighbor stabilized the serving p95 at 3ms (0 fails).