**W4D1 Lab: First Cluster**

**Predictions vs. Outcomes**
* **Node Location:** The single-node cluster runs directly as a process on the machine we are typing into, not inside a separate container or VM[cite: 1].
* **Health Check (503 vs 200):** The app returns 503 initially because it is waiting for the model backend to load into memory before it can safely serve requests[cite: 1]. 
* **Logs Comparison:** `kubectl logs serving` and `docker logs` produce the exact same output because the underlying container running the application has not changed[cite: 1].
* **Scheduler Refusal:** The refusal originating from the scheduler itself results in a `Pending` status (e.g., when a pod requests 64 CPUs on a node that only has 28)[cite: 1]. 

**Verification**

<img width="898" height="156" alt="Screenshot 2026-09-06 145132" src="https://github.com/user-attachments/assets/9f631c56-1739-4da0-b5ab-db498f2be277" />
