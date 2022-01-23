## Authorization

### Types
1. **Node Authorizer** - Kubelet running in a node has a specific set of permissions. Kubelets should be part of system nodes group and should be prefixed with `system node`. Any request from such a user will be authorized by the node authorizer.
2. **ABAC - Attribute Based Authorization Control** - Edit ploicy file and restart teh kubeapi server
3. **RBAC** - Role based accees
4. **Webhook**
5. **Always allow**
6. **Always deny**

--authorization-mode in kubeapi server specifies the types of allowed authorizations. If none is aspecified, it's always allow