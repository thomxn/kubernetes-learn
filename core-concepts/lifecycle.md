## Pod Status

|State           |Description   |
|----------------|--------------|
|Pending         |Scheduler is trying to find a node|
|ContinerCreating|Pulling images for containers|
|Running         | Currently executing|

## Pod Conditions

|Condition      |Description               |
|---------------|--------------------------|
|PodScheduled   |Pod is scheduled on a node|
|Initialized    |Pod is initialized        |
|ContainersReady|The containers are ready  |
|Ready          |The pod is ready          |

## Readiness

```
apiVersion: v1 
kind: Pod 
metadata:
  labels:
    name: webapp-pod
  name: webapp-pod
  namespace: default 
spec:
  containers:
  - image: kodekloud/simple-webapp-mysql
    imagePullPolicy: Always
    name: webapp
    readinessProbe:
    httpGet:
        path: /api/ready
        port: 8080
```

Alternatives for readinessProbe

```
readinessProbe:
    tcpSocket:
        port: 3306
```

```
readinessProbe:
    exec:
        command:
        - cat
        - /app/logs
```

Other options for readiness probe
1. `initialDelayInSeconds` - States that the container will take that specified no. of seconds to be ready
2. `periodSeconds` - How often to test the readiness probe
3. `failureThreshold` - Failure on first 3 probes will not probe the container anymore. This key overried the default value of 3

## Liveness
App is live and working nominally
Supprts all child nodes of `readinessProbe` just that the keyname is `livenessProbe`

## RestartPolicy

Decides whether to automatically restart a pod on termination. Default value is **Always**

`restartPolicy: Always | Never| OnFailure`


```
apiVersion: v1 
kind: Pod 
metadata:
  labels:
    name: webapp-pod
  name: webapp-pod
  namespace: default 
spec:
  containers:
  - image: kodekloud/simple-webapp-mysql
    name: webapp

  restartPolicy: OnFailure
```

