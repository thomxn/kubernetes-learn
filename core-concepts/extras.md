### Get count of pods matching a label

`kubectl get pods -l key=value --no-headers | wc -l`

`wc -l` gets the word count

### Get all k8 objects matching a label

`kubectl get pods all -l key=value`

### Select using multiple labels

`kubectl get pods -l env=prod,bu=dts`

### Execute command after every interval

`watch "command name"`
Ex: `watch free -m` to find free memory every 2 seconds

