# error


oward@howard-vm:~$ kubectl describe machinedeployment gpu-cluster-md-0
Name:         gpu-cluster-md-0
Namespace:    default
Labels:       cluster.x-k8s.io/cluster-name=gpu-cluster
Annotations:  machinedeployment.clusters.x-k8s.io/revision: 1
API Version:  cluster.x-k8s.io/v1beta1
Kind:         MachineDeployment
Metadata:
  Creation Timestamp:  2025-05-16T21:22:10Z
  Finalizers:
    cluster.x-k8s.io/machinedeployment
  Generation:  1
  Owner References:
    API Version:     cluster.x-k8s.io/v1beta1
    Kind:            Cluster
    Name:            gpu-cluster
    UID:             9b86952e-e1b4-4726-9a09-8c367a3c0c43
  Resource Version:  5346
  UID:               0a508710-1c54-47c0-b089-d35b6f38aaaf
Spec:
  Cluster Name:               gpu-cluster
  Min Ready Seconds:          0
  Progress Deadline Seconds:  600
  Replicas:                   1
  Revision History Limit:     1
  Selector:
    Match Labels:
      cluster.x-k8s.io/cluster-name:  gpu-cluster
  Strategy:
    Rolling Update:
      Max Surge:        1
      Max Unavailable:  0
    Type:               RollingUpdate
  Template:
    Metadata:
      Labels:
        cluster.x-k8s.io/cluster-name:  gpu-cluster
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
    Message:               Minimum availability requires 1 replicas, current 0 available
    Reason:                WaitingForAvailableMachines
    Severity:              Warning
    Status:                False
    Type:                  Ready
    Last Transition Time:  2025-05-16T21:22:11Z
    Message:               Minimum availability requires 1 replicas, current 0 available
    Reason:                WaitingForAvailableMachines
    Severity:              Warning
    Status:                False
    Type:                  Available
    Last Transition Time:  2025-05-16T21:22:11Z
    Message:               KubeadmControlPlane default/gpu-cluster-control-plane is provisioning ("ControlPlaneIsStable" preflight check failed)
    Reason:                PreflightCheckFailed
    Severity:              Error
    Status:                False
    Type:                  MachineSetReady
  Observed Generation:     1
  Phase:                   ScalingUp
  Selector:                cluster.x-k8s.io/cluster-name=gpu-cluster
  Unavailable Replicas:    1
  v1beta2:
    Available Replicas:  0
    Conditions:
      Last Transition Time:  2025-05-16T21:22:11Z
      Message:               0 available replicas, at least 1 required (spec.strategy.rollout.maxUnavailable is 0, spec.replicas is 1)
      Observed Generation:   1
      Reason:                NotAvailable
      Status:                False
      Type:                  Available
      Last Transition Time:  2025-05-16T21:22:11Z
      Message:               
      Observed Generation:   1
      Reason:                NotRollingOut
      Status:                False
      Type:                  RollingOut
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
      Message:               Scaling up from 0 to 1 replicas
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
Events:
  Type    Reason            Age   From                          Message
  ----    ------            ----  ----                          -------
  Normal  SuccessfulCreate  14m   machinedeployment-controller  Created MachineSet default/gpu-cluster-md-0-skzzp
