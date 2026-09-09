# Serving-Stack-Team5
### Shahad Alkhattaf

#### W4D4 – Helm and Autoscaling

- Deployed the serving stack with Helm and configured HPA.
- Tested the **Aggressive** autoscaling policy under load.

**Aggressive HPA Results**

- Target CPU: **30%**
- Replicas scaled: **1 → 4 → 5**
- Peak CPU: **400%**
- After load stopped, CPU dropped: **400% → 262% → 1% → 0%**
- Scale-in: **5 → 1**
- Scale-down stabilization window: **30s**

**Verification**

```text
scale event observed: desired replicas 1 -> 5
GREEN CHECK: PASS

#### W4D3 – Resource Policies and GPU Scheduling

- Verified CPU/GPU scheduling and resource limits.
- Deployed the shared vLLM engine on the GPU.

**Verification**

```text
team engine: Guaranteed, GPU visible inside the container, Service name safe
overdraft verified: Pending with 'Insufficient nvidia.com/gpu'
GREEN CHECK: PASS
```

#### W4D2 – Make It Self-Healing

**Self-Healing & Rolling Update**

* Deployment automatically replaced a deleted pod.
* Availability-first strategy: `maxUnavailable: 0`, `maxSurge: 1`.
* Rolling update completed with zero dropped requests.

**Verification**

```text id="mvy2r1"
PROBE RESULT ok=440 bad=0
rolling update completed with 440 requests served and none dropped
GREEN CHECK: PASS
```

#### W4D1 – First Cluster

**Pod Failure Diagnosis**
- `pod-a – ImagePullBackOff`: Image tag not found, so the image pull failed.
- `pod-b – Pending`: Insufficient CPU, so the scheduler could not place the pod.
- `pod-c – Error`: Container terminated with exit code 3.

**Verification**
```text
pod image: shahad00/aidc-serving:cpu-v1
evidence written to w4d1_evidence.json
GREEN CHECK: PASS
```

