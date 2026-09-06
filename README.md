# Serving-Stack-Team5
### Shahad Alkhattaf

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

