# dev_CloudNativeKubernetes
Kubernetes Development and Notes

#### Specialized Services
- kube-apiserver
  - Handles instructions sent to Kubernetes
    - accepts HTTPS requests, typically on port 443, presents cert which can be self-signed
    - presents authtentication, authorization mechanisms
    - will check with etcd and change if necessary
    = generally a Restful API with endpoints for each Kubernetes resource type, along with API version .. /api/v1

- kube-scheduler
  - Handles work of deciding which nodes to place workloads on
    - by default, this is inflenced by workload resource requirements, and note status

- kube-controller-manager
  - provides high-level control loop that ensures desired configuration of cluster and applications running on it is implemented
    - runs several controllers:
      - node controller, which ensures nodes are up and running
      - replication controller, ensures that workload is scaled properly
      - endpoints controller, handles communication and routing configuration for each workload
      - service account and token controllers, handles creation of API access tokens and default accounts

- etcd
  - distributed key-value store that contains cluster configuration
    - an etcd replica runs on each master node and uses Raft concensus algorithm to ensure a quorum is maintained before allowing changes
