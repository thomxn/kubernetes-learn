New rollout created a new revision

Use apply and set commands to update the deployment

`kubectl set image deployment deployment-name`

ex: `kubectl set image deployment/my-deployment nginx-container=nginx:1.12`

### Get rollout status 
`kubectl rollout status deployment deployment-name`

### Get rollout history 
`kubectl rollout history deployment deploymentname`

**Revision**

`kubectl rollout history deployment nginx --revision=1
`

### Change Cause

Change cause is the reason why a new revision was created. Inorder to do that use `--record` flag

Ex: `kubectl create -f deployment.yaml --record`

### Strategies
1. Recreate - Delete all pods and create new ones
2. Rolling - Replace pods one by one. This is the default strategy

Specify strategy in deployment definition as child of spec section

```
apiVersion: apps/v1
kind: Deployment
metadata:
  annotations:
    deployment.kubernetes.io/revision: "2"
  creationTimestamp: "2021-12-30T04:38:52Z"
  generation: 2
  name: frontend
  namespace: default
spec:
  minReadySeconds: 20
  progressDeadlineSeconds: 600
  replicas: 4
  revisionHistoryLimit: 10
  selector:
    matchLabels:
      name: webapp
  strategy:
    rollingUpdate:
      maxSurge: 25%
      maxUnavailable: 25%
    type: RollingUpdate
```

### Rollback

`kubectl rollout undo deployment deployment-name` will delete the new replicaset and restore the previous one


