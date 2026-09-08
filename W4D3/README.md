## Predict (by hand)

**1. If a pod requests 64 CPUs:**
The `kubectl apply` command will succeed without any errors, but the pod will be stuck in a `Pending` state forever. It won't crash because it never actually starts; the Kubernetes scheduler simply cannot find a node with enough CPU capacity to place it.

**2. Requesting a GPU when the only one is already taken:**
Just like the CPU scenario, the pod will stay in a `Pending` state. If we check the pod's events (via `kubectl describe pod`), the `FailedScheduling` error message will explicitly name the GPU constraint (e.g., "0/1 nodes are available: 1 Insufficient nvidia.com/gpu").

**3. Neighbor pod burning CPU (No limit vs. 500m limit):**
* **No limit:** The serving pod's latency becomes catastrophically worse. In our experiment, the p95 latency spiked to 5000ms and all requests failed because the neighbor starved the node.
* **With 500m limit:** The serving pod's latency returns to normal (stabilized at 3ms in our test). The system throttles the neighbor, ensuring the serving pod gets its guaranteed resources.

---

**[ GREEN CHECK: PASS ]** 
*(Insert image here)*