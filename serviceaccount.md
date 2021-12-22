Used by services to access kubernetes

`kubectl create serviceaccount servicename`
This will automatically create a token to this service account. This token is created a s secret object and linked to the serviceaccount
`/var/run/secret/kubernetes.io/serviceaccount` is the volumne where the secret is mounted