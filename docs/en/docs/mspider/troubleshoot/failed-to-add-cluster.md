# Hosted mesh is failed

## Question

- istio-ingressgateway does not work properly when hosted mesh is connected to new cluster.

     ??? note "Click to see the full error log"

          ```none
          [root@dce88 metallb]# kubectl describe pod istio-ingressgateway-b8b597c59-7gnwr -n istio-system
          Name: istio-ingressgateway-b8b597c59-7gnwr
          Namespace: istio-system
          Priority: 0
          Node: dce88/10.6.113.100
          Start Time: Fri, 24 Feb 2023 10:51:22 +0800
          Labels: app=istio-ingressgateway
                      chart=gateways
                      heritage=Tiller
                      install.operator.istio.io/owning-resource=unknown
                      istio=ingressgateway
                      istio.io/rev=default
                      operator.istio.io/component=IngressGateways
                      pod-template-hash=b8b597c59
                      release=istio
                      service.istio.io/canonical-name=istio-ingressgateway
                      service.istio.io/canonical-revision=latest
                      sidecar.istio.io/inject=false
          Annotations: prometheus.io/path: /stats/prometheus
                      prometheus.io/port: 15020
                      prometheus.io/scrape: true
                      sidecar.istio.io/inject: false
          Status: Running
          IP: 10.244.0.17
          IPs:
          IP: 10.244.0.17
          Controlled By: ReplicaSet/istio-ingressgateway-b8b597c59
          Containers:
          istio-proxy:
             Container ID: docker://40ef710d84433b108b58e8d286b46d6fde3f5ac2f6b7e80765d61aafb2d269da
             Image: 10.16.10.120/release.daocloud.io/mspider/proxyv2:1.16.1-mspider
             Image ID: docker-pullable://10.16.10.120/release.daocloud.io/mspider/proxyv2@sha256:4ac80ff62af5ebe7ebb5cb75d1b1f6791b55b56e1b45a0547197b26d9674fd22
             Ports: 15021/TCP, 8080/TCP, 8443/TCP, 15090/TCP
             Host Ports: 0/TCP, 0/TCP, 0/TCP, 0/TCP
             Args:
                proxy
                router
                --domain
                $(POD_NAMESPACE).svc.cluster.local
                --proxyLogLevel=warning
                --proxyComponentLogLevel=misc:error
                --log_output_level=default:info
             State: Running
                Started: Fri, 24 Feb 2023 10:51:25 +0800
             Ready: False
             Restart Count: 0
             Limits:
                cpu: 2
                memory: 1Gi
             Requests:
                cpu: 100m
                memory: 128Mi
             Readiness: http-get http://:15021/healthz/ready delay=1s timeout=1s period=2s #success=1 #failure=30
             Environment:
                JWT_POLICY: third-party-jwt
                PILOT_CERT_PROVIDER: istiod
                CA_ADDR: istiod.istio-system.svc:15012
                NODE_NAME: (v1:spec.nodeName)
                POD_NAME: istio-ingressgateway-b8b597c59-7gnwr (v1:metadata.name)
                POD_NAMESPACE: istio-system (v1:metadata.namespace)
                INSTANCE_IP: (v1:status.podIP)
                HOST_IP: (v1:status.hostIP)
                SERVICE_ACCOUNT: (v1:spec.serviceAccountName)
                ISTIO_META_WORKLOAD_NAME: istio-ingressgateway
                ISTIO_META_OWNER: kubernetes://apis/apps/v1/namespaces/istio-system/deployments/istio-ingressgateway
                ISTIO_META_MESH_ID: fupan-mesh
                TRUST_DOMAIN: cluster.local
                ISTIO_META_UNPRIVILEGED_POD: true
                ISTIO_META_DNS_AUTO_ALLOCATE: true
                ISTIO_META_DNS_CAPTURE: true
                ISTIO_META_CLUSTER_ID: futest-2
             Mounts:
                /etc/istio/config from config-volume (rw)
                /etc/istio/ingressgateway-ca-certs from ingressgateway-ca-certs (ro)
                /etc/istio/ingressgateway-certs from ingressgateway-certs (ro)
                /etc/istio/pod from podinfo (rw)
                /etc/istio/proxy from istio-envoy (rw)
                /var/lib/istio/data from istio-data (rw)
                /var/run/secrets/credential-uds from credential-socket (rw)
                /var/run/secrets/istio from istiod-ca-cert (rw)
                /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-hpgkx (ro)
                /var/run/secrets/tokens from istio-token (ro)
                /var/run/secrets/workload-spiffe-credentials from workload-certs (rw)
                /var/run/secrets/workload-spiffe-uds from workload-socket (rw)
          Conditions:
          Type Status
          Initialized True
          Ready False
          ContainersReady False
          PodScheduledTrue
          Volumes:
          workload-socket:
             Type: EmptyDir (a temporary directory that shares a pod's lifetime)
            Medium:     
            SizeLimit:  <unset>
         credential-socket:
            Type:       EmptyDir (a temporary directory that shares a pod's lifetime)
            Medium:     
            SizeLimit:  <unset>
         workload-certs:
            Type:       EmptyDir (a temporary directory that shares a pod's lifetime)
            Medium:     
            SizeLimit:  <unset>
         istiod-ca-cert:
            Type:      ConfigMap (a volume populated by a ConfigMap)
            Name:      istio-ca-root-cert
            Optional:  false
         podinfo:
            Type:  DownwardAPI (a volume populated by information about the pod)
            Items:
               metadata.labels -> labels
               metadata.annotations -> annotations
         istio-envoy:
            Type:       EmptyDir (a temporary directory that shares a pod's lifetime)
            Medium:     
            SizeLimit:  <unset>
         istio-data:
            Type:       EmptyDir (a temporary directory that shares a pod's lifetime)
            Medium:     
            SizeLimit:  <unset>
         istio-token:
            Type:                    Projected (a volume that contains injected data from multiple sources)
            TokenExpirationSeconds:  43200
         config-volume:
            Type:      ConfigMap (a volume populated by a ConfigMap)
            Name:      istio
            Optional:  true
         ingressgateway-certs:
            Type:        Secret (a volume populated by a Secret)
            SecretName:  istio-ingressgateway-certs
            Optional:    true
         ingressgateway-ca-certs:
            Type:        Secret (a volume populated by a Secret)
            SecretName:  istio-ingressgateway-ca-certs
            Optional:    true
         kube-api-access-hpgkx:
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
         Type     Reason     Age                 From               Message
         ----     ------     ----                ----               -------
         Normal   Scheduled  63s                 default-scheduler  Successfully assigned istio-system/istio-ingressgateway-b8b597c59-7gnwr to dce88
         Normal   Pulled     62s                 kubelet            Container image "10.16.10.120/release.daocloud.io/mspider/proxyv2:1.16.1-mspider" already present on machine
         Normal   Created    60s                 kubelet            Created container istio-proxy
         Normal   Started    60s                 kubelet            Started container istio-proxy
         Warning  Unhealthy  19s (x22 over 59s)  kubelet            Readiness probe failed: Get "http://10.244.0.17:15021/healthz/ready": dial tcp 10.244.0.17:15021: connect: connection refused
         ```

- The istiod-remote ep ip assignment is wrong in the case where the control plane and data plane of the hosted mesh are deployed together.

     When the managed cluster is connected to the hosted mesh as a workload cluster, the istiod-remote ep ip is allocated as metalLB IP, which should be PodIP (mspider-mcpc-ckube-remote-xxx)

    ![istiod-remote](https://docs.daocloud.io/daocloud-docs-images/docs/mspider/troubleshoot/images/add-cluster01.png)

## Cause Analysis

1. Case 1: The managed cluster does not have metalLB installed, resulting in a cluster network failure, ingressgateway cannot normally allocate endpoints and CrashLoopBackoff

2. Case 2: The endpoint allocation of the istio-remote component is wrong, run `kubectl get ep -n istio-system` to view the details

## Solution

1. Case 1: addon deploys metalLB
2. Scenario 2: Check

     1. Control plane cluster `istio-remote ep: istio-${meshID}-hosted ${podIP}:15012/15017`
     2. Workload cluster `istio-remote ep: istiod-hosted-mesh-hosted-lb ${loadBalancerIP}:15012/15017`