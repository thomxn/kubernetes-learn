## Services

Enables communication between pod groups

`kubectl create service nodeport ingress --tcp=80:80`

### Types 

1. NodePort: Listens on a port in a node and forwards the request
2. ClusterIP: Creates a virtual IP inside the cluster to enable inter-communication. This is the default type
3. LoadBalancer: Balances the load

### Ports

1. TargetPort: Port exposed by the Pod
2. Port: Port of the service
3. NodePort: Port exposed by the Node running the pods

### NodePort

```
apiVersion: v1
kind: Service
metadata:
    name: service
spec:
    type: NodePort
    ports:
    - targetPort: 80
      port: 80
      nodePort: 30008
    selector:
        app: myapp
        type: front-end
```

If unspecified, `targetPort` will assume the value specified in the `port` key. Similarly, `nodePort` will be assigned a random free port in the range of  30000 - 32767


### ClusterIP

```
apiVersion: v1
kind: Service
metadata:
    name: service
spec:
    type: ClusterIP #
    ports:
    - targetPort: 80
      port: 80
    selector:
        app: myapp
        type: front-end
```
