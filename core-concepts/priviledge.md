## Run comtainer as a specific user and

`docker run --user=1000 ubuntu sleep 100`

or use
```
FROM ubuntu

USER 1000
```

## Add extra permission to the process running the container

docker run --cap-add KILL ubuntu
docker run --cap-drop KILL ubuntu

## For all priviledges

docker run --priviledged ubuntu


kubectl create secret generic db-secret --from-literal=DB_Host=sql01 --from-literal=DB_User=root --from-literal=DB_Password=password123

Privilege can be configured in `Pod` level or `Container` level

Run the command: `kubectl exec ubuntu-sleeper -- whoami` and check the user that is running the container.