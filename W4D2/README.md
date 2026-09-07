**W4D2 Lab: Make it Self-Healing**

**Predictions vs. Measurements**
* Kill Demo: Predicted 0 dropped requests, measured 0[cite: 1].
* Rolling Update (with preStop & probes): Predicted 0 dropped, measured 0[cite: 1].
* Rolling Update (without preStop): Predicted 2 dropped, measured 2[cite: 1].
* Constraint Roll: Predicted 0 dropped, measured 0 (Accepted)[cite: 1].

**Constraint Card**
* Card: A (Availability first)[cite: 1].
* Settings: `maxUnavailable: 0`, `maxSurge: 1`[cite: 1, 2].
* Measured Failures: 0[cite: 1].
* Sign-off: Yes, the primary requirement of zero downtime was successfully met[cite: 1].

**Verification**

<img width="615" height="122" alt="Screenshot 2026-09-07 163901" src="https://github.com/user-attachments/assets/a751ac69-589c-4a5d-b692-79c969e1477d" />
