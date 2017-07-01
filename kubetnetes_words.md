# Words of kubernetes
node
- host server
- 1 node = 1 Virtual Machine

cluster
- aggregation of nodes

pod
- aggregation of containers = 1 application
    - reverse proxy 
    - web application
- minimum unit to deploy by k8s
- pod runs on node
- containers of pod are co-sheduled
- containers of pod are co-located = deploy on 1 node

container
- 1 container = 1 process of linux machine

Selector
- using "Label" to control target group
    - label example : role = web
Service
- 1 service = multiple pod = multiple application
- "Service Discovery" using DNS record. 
    - ex: web.default.svc.cluster.local
- service are defined name(=DNS record) and selectoer(=label)
    - name: web
    - role: web
- types of Service
    - ClusterIP     : DNS name or Virtual IP address on cluster
    - NodePort      : publish static port number using ClusterIP
    - LoadBalancer  : make load balancer and link to service using NodePort
    - ExternalName  : To use exernal services, make alias for internal cluster using DNS CNAME.
    - Headless      : To use "StatefulSet" function, make DNS SRV record of pod to DNS name resolution.