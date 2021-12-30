The default resorce units for a pod or a container within a pod are
1. CPU: 0.5
2. Memory: 256 MB

This is called a resource request for a container

The lowest value in units is `0.1` which can also be represented as `100m`
The lowest value in milli representation is `1m`

Use limits to limit the resourcce usage of a container
If a pod consistenty consumes more memory than the limit consistently, the Pod will be terminated

## Taints and Tolerance

Taints are set on Nodes and tolerations are set on Pods

taint-effects control the behaviour when the pod is not tolerant to the node
1. `NoSchedule` : The pod will not be scheduled
2. `PreferNoSchedule` : The pod will not be placed, but it's not guranteed!
3. `NoExecute`: The executing pods will be terminated, if it doesnot tolerate the taint

`kubectl taint nodes node-name app=blue:NoSchedule`

To untaint a node use - at the end

`kubectl taint nodes node-name app=blue:NoSchedule-`

_All the values in the `tolerations` key should be in quotes_
### Update the pod definition to add the toleration
```
apiVersion: v1
kind: Pod
metadata:
  name: resource
  labels:
    type: demo
spec:
  containers:
  - image: nginx
    name: demo-container
    tolerations:
    - key: "app"
      operator: "Equal"
      value: "blue"
      effect: "NoSchedule"
```

## Node Affinity

Empowers the pod to select the host node. Label is used to this selection

First, label the node
`kubectl label nodes node-name key=value`

```
apiVersion: v1
kind: Pod
metadata:
  name: resource
  labels:
    type: demo
spec:
  containers:
  - image: nginx
    name: demo-container
  nodeSelector:
    key: value
```

## Node Affinity

To ensure pods are hosted in particular nodes


```
apiVersion: v1
kind: Pod
metadata:
  name: resource
  labels:
    type: demo
spec:
  containers:
  - image: nginx
    name: demo-container
  affinity:
    nodeAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
        nodeSelectorTerms:
        - matchExpressions:
          - key: keyName
            operator: NotIn
            values:
            - medium
              large
```

`requiredDuringSchedulingIgnoredDuringExecution` or `preferredDuringSchedulingIgnoredDuringExecution`

Label node via cli 

`kubectl label node node01 color=blue`

Get pod detailed overview using woide output
`kubectl get pods -o wide`