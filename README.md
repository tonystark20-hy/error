# error

howard@howard-vm:~$ kubectl describe kubeadmcontrolplane -n default gpu-cluster-control-plane
Name:         gpu-cluster-control-plane
Namespace:    default
Labels:       cluster.x-k8s.io/cluster-name=gpu-cluster
Annotations:  <none>
API Version:  controlplane.cluster.x-k8s.io/v1beta1
Kind:         KubeadmControlPlane
Metadata:
  Creation Timestamp:  2025-05-16T21:20:10Z
  Finalizers:
    kubeadm.controlplane.cluster.x-k8s.io
  Generation:  1
  Owner References:
    API Version:           cluster.x-k8s.io/v1beta1
    Block Owner Deletion:  true
    Controller:            true
    Kind:                  Cluster
    Name:                  gpu-cluster
    UID:                   9b86952e-e1b4-4726-9a09-8c367a3c0c43
  Resource Version:        5333
  UID:                     5b8bf248-0584-4963-b11a-8cbe5c514611
Spec:
  Kubeadm Config Spec:
    Cluster Configuration:
      API Server:
        Extra Args:
          Anonymous - Auth:                              true
          Authorization - Mode:                          RBAC,Node
          Default - Not - Ready - Toleration - Seconds:  60
          Default - Unreachable - Toleration - Seconds:  60
          Disable - Admission - Plugins:                 AlwaysAdmit
          Enable - Admission - Plugins:                  AlwaysPullImages,NamespaceLifecycle,ServiceAccount,NodeRestriction
        Timeout For Control Plane:                       10m0s
      Controller Manager:
        Extra Args:
          Feature - Gates:                        RotateKubeletServerCertificate=true
          Pod - Eviction - Timeout:               1m0s
          Terminated - Pod - Gc - Threshold:      25
          Use - Service - Account - Credentials:  true
      Dns:
      Etcd:
      Networking:
      Scheduler:
    Format:  cloud-config
    Init Configuration:
      Local API Endpoint:
      Node Registration:
        Image Pull Policy:  IfNotPresent
        Kubelet Extra Args:
          Event - Qps:         0
          Feature - Gates:     RotateKubeletServerCertificate=true
          Read - Only - Port:  0
        Name:                  {{ v1.local_hostname }}
    Join Configuration:
      Control Plane:
        Local API Endpoint:
      Discovery:
      Node Registration:
        Image Pull Policy:  IfNotPresent
        Kubelet Extra Args:
          Event - Qps:         0
          Feature - Gates:     RotateKubeletServerCertificate=true
          Read - Only - Port:  0
        Name:                  {{ v1.local_hostname }}
    Pre Kubeadm Commands:
      while [ ! -S /var/run/containerd/containerd.sock ]; do echo 'Waiting for containerd...'; sleep 1; done
      sed -ri '/\sswap\s/s/^#?/#/' /etc/fstab
      swapoff -a
    Use Experimental Retry Join:  true
  Machine Template:
    Infrastructure Ref:
      API Version:  infrastructure.cluster.x-k8s.io/v1beta1
      Kind:         MaasMachineTemplate
      Name:         gpu-cluster-control-plane
      Namespace:    default
    Metadata:
  Replicas:  1
  Rollout Strategy:
    Rolling Update:
      Max Surge:  1
    Type:         RollingUpdate
  Version:        v1.32.4
Status:
  Conditions:
    Last Transition Time:  2025-05-16T21:22:11Z
    Message:               Scaling up control plane to 1 replicas (actual 0)
    Reason:                ScalingUp
    Severity:              Warning
    Status:                False
    Type:                  Ready
    Last Transition Time:  2025-05-16T21:22:11Z
    Message:               Scaling up control plane to 1 replicas (actual 0)
    Reason:                ScalingUp
    Severity:              Warning
    Status:                False
    Type:                  Resized
  Observed Generation:     1
  Selector:                cluster.x-k8s.io/cluster-name=gpu-cluster,cluster.x-k8s.io/control-plane
  v1beta2:
    Available Replicas:  0
    Conditions:
      Last Transition Time:  2025-05-16T21:22:11Z
      Message:               Control plane not yet initialized
      Observed Generation:   1
      Reason:                NotAvailable
      Status:                False
      Type:                  Available
      Last Transition Time:  2025-05-16T21:22:11Z
      Message:               
      Observed Generation:   1
      Reason:                NotInitialized
      Status:                False
      Type:                  Initialized
      Last Transition Time:  2025-05-16T21:22:11Z
      Message:               Waiting for Cluster status.infrastructureReady to be true
      Observed Generation:   1
      Reason:                InspectionFailed
      Status:                Unknown
      Type:                  EtcdClusterHealthy
      Last Transition Time:  2025-05-16T21:22:11Z
      Message:               Waiting for Cluster status.infrastructureReady to be true
      Observed Generation:   1
      Reason:                InspectionFailed
      Status:                Unknown
      Type:                  ControlPlaneComponentsHealthy
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
Events:                      <none>
