# error
Name:             capmaas-controller-manager-574ff49ffb-hgrs7
Namespace:        capmaas-system
Priority:         0
Service Account:  default
Node:             howard-vm/172.31.3.233
Start Time:       Thu, 15 May 2025 08:19:24 +0800
Labels:           cluster.x-k8s.io/provider=infrastructure-maas
                  control-plane=controller-manager
                  pod-template-hash=574ff49ffb
Annotations:      <none>
Status:           Pending
IP:               10.244.0.12
IPs:
  IP:           10.244.0.12
Controlled By:  ReplicaSet/capmaas-controller-manager-574ff49ffb
Containers:
  manager:
    Container ID:  
    Image:         gcr.io/spectro-dev-public/release/cluster-api/cluster-api-provider-maas-controller:v0.6.1
    Image ID:      
    Port:          9443/TCP
    Host Port:     0/TCP
    Command:
      /manager
    Args:
      --metrics-bind-addr=127.0.0.1:8080
      --leader-elect
    State:          Waiting
      Reason:       ImagePullBackOff
    Ready:          False
    Restart Count:  0
    Limits:
      cpu:     200m
      memory:  100Mi
    Requests:
      cpu:     200m
      memory:  20Mi
    Environment:
      MAAS_ENDPOINT:  <set to the key 'MAAS_ENDPOINT' in secret 'capmaas-manager-bootstrap-credentials'>  Optional: false
      MAAS_API_KEY:   <set to the key 'MAAS_API_KEY' in secret 'capmaas-manager-bootstrap-credentials'>   Optional: false
    Mounts:
      /tmp/k8s-webhook-server/serving-certs from cert (ro)
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-v2clt (ro)
  kube-rbac-proxy:
    Container ID:  containerd://8ad31b1a31c131e9c2e8a81f322853998bea75dc1d23d3f4d2a48ef2bdc71897
    Image:         gcr.io/kubebuilder/kube-rbac-proxy:v0.5.0
    Image ID:      gcr.io/kubebuilder/kube-rbac-proxy@sha256:e10d1d982dd653db74ca87a1d1ad017bc5ef1aeb651bdea089debf16485b080b
    Port:          8443/TCP
    Host Port:     0/TCP
    Args:
      --secure-listen-address=0.0.0.0:8443
      --upstream=http://127.0.0.1:8080/
      --logtostderr=true
      --v=10
    State:          Running
      Started:      Thu, 15 May 2025 08:19:42 +0800
    Ready:          True
    Restart Count:  0
    Environment:    <none>
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-v2clt (ro)
Conditions:
  Type                        Status
  PodReadyToStartContainers   True 
  Initialized                 True 
  Ready                       False 
  ContainersReady             False 
  PodScheduled                True 
Volumes:
  cert:
    Type:        Secret (a volume populated by a Secret)
    SecretName:  webhook-server-cert
    Optional:    false
  kube-api-access-v2clt:
    Type:                    Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:  3607
    ConfigMapName:           kube-root-ca.crt
    ConfigMapOptional:       <nil>
    DownwardAPI:             true
QoS Class:                   Burstable
Node-Selectors:              <none>
Tolerations:                 node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                             node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type     Reason   Age                  From     Message
  ----     ------   ----                 ----     -------
  Normal   BackOff  67s (x395 over 91m)  kubelet  Back-off pulling image "gcr.io/spectro-dev-public/release/cluster-api/cluster-api-provider-maas-controller:v0.6.1"
  Warning  Failed   67s (x395 over 91m)  kubelet  Error: ImagePullBackOff
