# error

apiVersion: infrastructure.cluster.x-k8s.io/v1beta1
kind: MaasCluster
metadata:
name: gpu-cluster
namespace: default
annotations:
"helm.sh/resource-policy": keep
spec:
dnsDomain: example.com
---
apiVersion: cluster.x-k8s.io/v1beta1
kind: Cluster
metadata:
name: gpu-cluster
namespace: default
spec:
clusterNetwork:
pods:
cidrBlocks:
- 192.168.0.0/16
serviceDomain: cluster.local
services:
cidrBlocks:
- 10.96.0.0/12
controlPlaneRef:
apiVersion: controlplane.cluster.x-k8s.io/v1beta1
kind: KubeadmControlPlane
name: gpu-cluster-control-plane
infrastructureRef:
apiVersion: infrastructure.cluster.x-k8s.io/v1beta1
kind: MaasCluster
name: gpu-cluster
---
apiVersion: infrastructure.cluster.x-k8s.io/v1beta1
kind: MaasMachineTemplate
Kubernetes Page 8
kind: MaasMachineTemplate
metadata:
name: gpu-cluster-control-plane
namespace: default
spec:
template:
spec:
image: custom/ubuntu-2204-k8s-1.26.1
minCPU: 4
minMemory: 8192
resourcePool: CPU
tags:
- dell
---
apiVersion: controlplane.cluster.x-k8s.io/v1beta1
kind: KubeadmControlPlane
metadata:
name: gpu-cluster-control-plane
namespace: default
annotations:
"helm.sh/resource-policy": keep
spec:
kubeadmConfigSpec:
clusterConfiguration:
apiServer:
extraArgs:
anonymous-auth: "true"
authorization-mode: RBAC,Node
default-not-ready-toleration-seconds: "60"
default-unreachable-toleration-seconds: "60"
disable-admission-plugins: AlwaysAdmit
enable-admission-plugins: AlwaysPullImages,NamespaceLifecycle,ServiceAccount,NodeRestriction
timeoutForControlPlane: 10m0s
controllerManager:
extraArgs:
feature-gates: RotateKubeletServerCertificate=true
pod-eviction-timeout: 1m0s
terminated-pod-gc-threshold: "25"
use-service-account-credentials: "true"
dns: {}
etcd: {}
networking: {}
scheduler:
extraArgs: null
initConfiguration:
localAPIEndpoint:
advertiseAddress: ""
bindPort: 0
nodeRegistration:
kubeletExtraArgs:
event-qps: "0"
feature-gates: RotateKubeletServerCertificate=true
read-only-port: "0"
name: '{{ v1.local_hostname }}'
joinConfiguration:
controlPlane:
localAPIEndpoint:
advertiseAddress: ""
bindPort: 0
discovery: {}
nodeRegistration:
kubeletExtraArgs:
event-qps: "0"
feature-gates: RotateKubeletServerCertificate=true
read-only-port: "0"
name: '{{ v1.local_hostname }}'
preKubeadmCommands:
- while [ ! -S /var/run/containerd/containerd.sock ]; do echo 'Waiting for containerd...';
sleep 1; done
- sed -ri '/\sswap\s/s/^#?/#/' /etc/fstab
- swapoff -a
useExperimentalRetryJoin: true
machineTemplate:
infrastructureRef:
apiVersion: infrastructure.cluster.x-k8s.io/v1beta1
Kubernetes Page 9
apiVersion: infrastructure.cluster.x-k8s.io/v1beta1
kind: MaasMachineTemplate
name: gpu-cluster-control-plane
replicas: 1
version: v1.26.1
---
apiVersion: infrastructure.cluster.x-k8s.io/v1beta1
kind: MaasMachineTemplate
metadata:
name: gpu-cluster-md-0
namespace: default
spec:
template:
spec:
image: custom/ubuntu-2204-k8s-1.26.1
minCPU: 4
minMemory: 8192
resourcePool: GPU
tags:
- dell
---
apiVersion: cluster.x-k8s.io/v1beta1
kind: MachineDeployment
metadata:
name: gpu-cluster-md-0
namespace: default
annotations:
"helm.sh/resource-policy": keep
spec:
clusterName: gpu-cluster
replicas: 1
selector:
matchLabels:
cluster.x-k8s.io/cluster-name: gpu-cluster
template:
spec:
bootstrap:
configRef:
apiVersion: bootstrap.cluster.x-k8s.io/v1beta1
kind: KubeadmConfigTemplate
name: gpu-cluster-md-0
clusterName: gpu-cluster
infrastructureRef:
apiVersion: infrastructure.cluster.x-k8s.io/v1beta1
kind: MaasMachineTemplate
name: gpu-cluster-md-0
version: v1.26.1
---
apiVersion: bootstrap.cluster.x-k8s.io/v1beta1
kind: KubeadmConfigTemplate
metadata:
name: gpu-cluster-md-0
namespace: default
spec:
template:
spec:
joinConfiguration:
nodeRegistration:
kubeletExtraArgs:
event-qps: "0"
feature-gates: RotateKubeletServerCertificate=true
read-only-port: "0"
name: '{{ v1.local_hostname }}'
preKubeadmCommands:
- while [ ! -S /var/run/containerd/containerd.sock ]; do echo 'Waiting for containerd...';
sleep 1; done
- sed -ri '/\sswap\s/s/^#?/#/' /etc/fstab
- swapoff -a
useExperimentalRetryJoin: true
