
howard@howard-vm:~$ clusterctl generate cluster gpu-cluster --infrastructure=maas:v0.5.0 --kubernetes-version=1.32.4 --control-plane-machine-count=1 --worker-machine-count=1 | kubectl apply -f -
maascluster.infrastructure.cluster.x-k8s.io/gpu-cluster created
maasmachinetemplate.infrastructure.cluster.x-k8s.io/gpu-cluster-control-plane created
kubeadmcontrolplane.controlplane.cluster.x-k8s.io/gpu-cluster-control-plane created
maasmachinetemplate.infrastructure.cluster.x-k8s.io/gpu-cluster-md-0 created
kubeadmconfigtemplate.bootstrap.cluster.x-k8s.io/gpu-cluster-md-0 created
Error from server (InternalError): error when creating "STDIN": Internal error occurred: failed calling webhook "default.cluster.cluster.x-k8s.io": failed to call webhook: Post "https://capi-webhook-service.cattle-provisioning-capi-system.svc:443/mutate-cluster-x-k8s-io-v1beta1-cluster?timeout=10s": service "capi-webhook-service" not found
Error from server (InternalError): error when creating "STDIN": Internal error occurred: failed calling webhook "default.machinedeployment.cluster.x-k8s.io": failed to call webhook: Post "https://capi-webhook-service.cattle-provisioning-capi-system.svc:443/mutate-cluster-x-k8s-io-v1beta1-machinedeployment?timeout=10s": service "capi-webhook-service" not found
howard@howard-vm:~$ kubectl get svc -n capmaas-system
NAME                                         TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)    AGE
capmaas-controller-manager-metrics-service   ClusterIP   10.109.165.97    <none>        8443/TCP   2m
capmaas-webhook-service                      ClusterIP   10.107.179.113   <none>        443/TCP    2m
