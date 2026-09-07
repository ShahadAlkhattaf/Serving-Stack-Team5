# Serving-Stack-Team5
### Shahad Alkhattaf

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

