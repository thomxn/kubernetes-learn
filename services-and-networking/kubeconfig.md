### Set current context
`kubectl config --kubeconfig=/root/my-kube-config use-context research`

Use kubectl proxy to connect to api server without specifying the cert

OR

curl http://localhost:6443 -k --key=admin.key --cert=admin.crt --cacert=ca.crt

Role and RoleBinding is used to map RBAC

## Check Access

`kubectl auth can-i create deployments`

**Impersonate as dev-user in namespace**
`kubectl auth can-i create deployments --as dev-user --namespace prod`

Use resource names to limit access to specific resources such as pods

```
kind: Role
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  namespace: blue
  name: deploy-role
rules:
- apiGroups: ["apps", "extensions"] #NOTE ARRAY
  resources: ["deployments"]
  verbs: ["create"]
```