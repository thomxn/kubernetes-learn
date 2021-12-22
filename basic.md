kubectl config set-context $(kubectl config current-context) --namespace --dev

kubectl get pods --all-namespaces

You can also scale a deployment using the kubectl scale command.

kubectl expose pod redis --port=6379 --name redis-service

kubectl create deployment webapp --image=kodekloud/webapp-color --replicas=3

kubectl create ns dev-ns

Create a pod called httpd using the image httpd:alpine in the default namespace. Next, create a service of type ClusterIP by the same name (httpd). The target port for the service should be 80.
`kubectl run httpd --image=httpd:alpine --port=80 --expose`