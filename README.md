# error

 howard@howard-vm:~$ kubectl describe maascluster n default gpu-cluster
Name:         gpu-cluster
Namespace:    default
Labels:       cluster.x-k8s.io/cluster-name=gpu-cluster
Annotations:  <none>
API Version:  infrastructure.cluster.x-k8s.io/v1beta1
Kind:         MaasCluster
Metadata:
  Creation Timestamp:  2025-05-16T21:20:10Z
  Finalizers:
    maascluster.infrastructure.cluster.x-k8s.io
  Generation:  1
  Owner References:
    API Version:           cluster.x-k8s.io/v1beta1
    Block Owner Deletion:  true
    Controller:            true
    Kind:                  Cluster
    Name:                  gpu-cluster
    UID:                   9b86952e-e1b4-4726-9a09-8c367a3c0c43
  Resource Version:        5332
  UID:                     068642c4-ddf8-477f-8459-ff02ec9be7c9
Spec:
  Control Plane Endpoint:
    Host:      
    Port:      0
  Dns Domain:  maas
Status:
  Conditions:
    Last Transition Time:  2025-05-16T21:22:11Z
    Message:               0 of 2 completed
    Reason:                LoadBalancerFailed
    Severity:              Error
    Status:                False
    Type:                  Ready
    Last Transition Time:  2025-05-16T21:22:11Z
    Message:               error retrieving dns resources "gpu-cluster-1d09c5.maas": status: 401, message: Authorization Error: Invalid API key.
    Reason:                LoadBalancerFailed
    Severity:              Error
    Status:                False
    Type:                  LoadBalancerReady
  Network:
    Dns Name:  gpu-cluster-1d09c5.maas
  Ready:       false
Events:        <none>
Error from server (NotFound): maasclusters.infrastructure.cluster.x-k8s.io "n" not found
Error from server (NotFound): maasclusters.infrastructure.cluster.x-k8s.io "default" not found
howard@howard-vm:~$ 
