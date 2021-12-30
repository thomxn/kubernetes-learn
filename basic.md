kubectl config set-context $(kubectl config current-context) --namespace --dev

kubectl get pods --all-namespaces

You can also scale a deployment using the kubectl scale command.

kubectl expose pod redis --port=6379 --name redis-service

kubectl create deployment webapp --image=kodekloud/webapp-color --replicas=3

### Get API doc

`kubectl explain job --recursive | less`

### Create namespace

kubectl create ns dev-ns

Create a pod called httpd using the image httpd:alpine in the default namespace. Next, create a service of type ClusterIP by the same name (httpd). The target port for the service should be 80.
`kubectl run httpd --image=httpd:alpine --port=80 --expose`

## Multi container pods

The definitions are wrt a logging example
1. Sidecar - Logs the server
2. Adapter - Converts the logs
3. Ambassador - Decides which db to connect to

## Logs

Get log from a pod
`kubectl -n elastic-stack exec -it app -- cat /log/app.log`

OR 

`kubectl logs podname containername-in-the-pod`

For live logs use -f 

`kubectl logs -f pod-name`

**Metrics Server** is an in-memory logger. Metrics is obtained from `**cAdvisor** component inside the **Kubelet** service running in a node

`kubectl top node`

`kubectl top pod`

`kubectl top pod --sort-by='memory' --no-headers | head -1`

## Labels and Selectors

`kubectl get pod --selector key=value`

Example `kubectl get pods --selector type=frontend`

### Annotations

They are used to capture extra information such as build number, contact info etc. and goes to he same level as `labels`

```
annotations:
    buildversion: 1.6.3
```