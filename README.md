# error

howard@howard-vm:~$ kubectl describe machineset -n default gpu-cluster-md-0-skzzp
Name:         gpu-cluster-md-0-skzzp
Namespace:    default
Labels:       cluster.x-k8s.io/cluster-name=gpu-cluster
              cluster.x-k8s.io/deployment-name=gpu-cluster-md-0
              machine-template-hash=2814603425-skzzp
Annotations:  machinedeployment.clusters.x-k8s.io/desired-replicas: 1
              machinedeployment.clusters.x-k8s.io/max-replicas: 2
              machinedeployment.clusters.x-k8s.io/revision: 1
API Version:  cluster.x-k8s.io/v1beta1
Kind:         MachineSet
Metadata:
  Creation Timestamp:  2025-05-16T21:22:11Z
  Finalizers:
    cluster.x-k8s.io/machineset
  Generation:  1
  Owner References:
    API Version:           cluster.x-k8s.io/v1beta1
    Block Owner Deletion:  true
    Controller:            true
    Kind:                  MachineDeployment
    Name:                  gpu-cluster-md-0
    UID:                   0a508710-1c54-47c0-b089-d35b6f38aaaf
  Resource Version:        5343
  UID:                     e81d6ad1-e924-4bf2-978f-a3af15e4d99e
Spec:
  Cluster Name:   gpu-cluster
  Delete Policy:  Random
  Replicas:       1
  Selector:
    Match Labels:
      cluster.x-k8s.io/cluster-name:  gpu-cluster
      Machine - Template - Hash:      2814603425-skzzp
  Template:
    Metadata:
      Labels:
        cluster.x-k8s.io/cluster-name:  gpu-cluster
        Machine - Template - Hash:      2814603425-skzzp
    Spec:
      Bootstrap:
        Config Ref:
          API Version:  bootstrap.cluster.x-k8s.io/v1beta1
          Kind:         KubeadmConfigTemplate
          Name:         gpu-cluster-md-0
          Namespace:    default
      Cluster Name:     gpu-cluster
      Infrastructure Ref:
        API Version:  infrastructure.cluster.x-k8s.io/v1beta1
        Kind:         MaasMachineTemplate
        Name:         gpu-cluster-md-0
        Namespace:    default
      Version:        v1.32.4
Status:
  Conditions:
    Last Transition Time:  2025-05-16T21:22:11Z
    Message:               KubeadmControlPlane default/gpu-cluster-control-plane is provisioning ("ControlPlaneIsStable" preflight check failed)
    Reason:                PreflightCheckFailed
    Severity:              Error
    Status:                False
    Type:                  Ready
    Last Transition Time:  2025-05-16T21:22:11Z
    Message:               KubeadmControlPlane default/gpu-cluster-control-plane is provisioning ("ControlPlaneIsStable" preflight check failed)
    Reason:                PreflightCheckFailed
    Severity:              Error
    Status:                False
    Type:                  MachinesCreated
    Last Transition Time:  2025-05-16T21:22:11Z
    Message:               Scaling up MachineSet to 1 replicas (actual 0)
    Reason:                ScalingUp
    Severity:              Warning
    Status:                False
    Type:                  Resized
  Observed Generation:     1
  Selector:                cluster.x-k8s.io/cluster-name=gpu-cluster,machine-template-hash=2814603425-skzzp
  v1beta2:
    Available Replicas:  0
    Conditions:
      Last Transition Time:  2025-05-16T21:22:11Z
      Message:               
      Observed Generation:   1
      Reason:                NotRemediating
      Status:                False
      Type:                  Remediating
      Last Transition Time:  2025-05-16T21:22:11Z
      Message:               
      Observed Generation:   1
      Reason:                NotScalingDown
      Status:                False
      Type:                  ScalingDown
      Last Transition Time:  2025-05-16T21:22:11Z
      Message:               Scaling up from 0 to 1 replicas is blocked because:
* KubeadmControlPlane default/gpu-cluster-control-plane is provisioning ("ControlPlaneIsStable" preflight check failed)
      Observed Generation:   1
      Reason:                ScalingUp
      Status:                True
      Type:                  ScalingUp
      Last Transition Time:  2025-05-16T21:22:11Z
      Message:               
      Observed Generation:   1
      Reason:                NoReplicas
      Status:                True
      Type:                  MachinesReady
      Last Transition Time:  2025-05-16T21:22:11Z
      Message:               
      Observed Generation:   1
      Reason:                NoReplicas
      Status:                True
      Type:                  MachinesUpToDate
      Last Transition Time:  2025-05-16T21:22:11Z
      Message:               
      Observed Generation:   1
      Reason:                NotPaused
      Status:                False
      Type:                  Paused
      Last Transition Time:  2025-05-16T21:22:11Z
      Message:               
      Observed Generation:   1
      Reason:                NotDeleting
      Status:                False
      Type:                  Deleting
    Ready Replicas:          0
    Up To Date Replicas:     0
Events:                      <none>
