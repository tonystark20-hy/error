# error
  GNU nano 6.2                      t-cluster.yaml                                
    name: t-cluster-control-plane
  infrastructureRef:
    apiVersion: infrastructure.cluster.x-k8s.io/v1beta1
    kind: MaasCluster
    name: t-cluster
---
apiVersion: infrastructure.cluster.x-k8s.io/v1beta1
kind: MaasMachineTemplate
metadata:
  name: t-cluster-control-plane
  namespace: default
spec:
  template:
    spec:
      image: custom/u2204-k1-32-4
      minCPU: 4
      minMemory: 8192
      resourcePool: default

