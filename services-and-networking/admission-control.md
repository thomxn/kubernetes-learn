Check enable-admission-plugins in /etc/kubernetes/manifests/kube-apiserver.yaml
to find which admission controller is enabled

`- --disable-admission-plugins=DefaultStorageClass` to disable **DefaultStorageClass**


Since the kube-apiserver is running as pod you can check the process to see enabled and disabled plugins.

`ps -ef | grep kube-apiserver | grep admission-plugins`

1. Mutating Admission Controller
2. Validating Admission Controller