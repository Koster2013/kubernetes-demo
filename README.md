
### Step One: Turn up the UX for the demo

[infos](../../../docs/user-guide/kubectl/kubectl_proxy.md).

```
$ kubectl proxy --www=kubernetes-demo/local/ &
+ kubectl proxy --www=kubernetes-demo/local/
I0218 15:18:31.623279   67480 proxy.go:36] Starting to serve on localhost:8001
```

Now visit the the [demo website](http://172.17.8.101:8001/static).  You won't see anything much quite yet.

### Step Two: Run the replication controller

```bash
$ kubectl create -f kubernetes-demo/jboss-rc.yaml
```

### Step Three: Try scaling the replication controller

```bash
$ kubectl scale rc update-demo-jboss --replicas=4
```

### Step Four: Update the docker image

```bash
$ kubectl rolling-update update-demo-jboss --update-period=10s -f kubernetes-demo/glassfish-rc.yaml
```

### Step Five: Bring down the pods

```bash
$ kubectl stop rc update-demo-glassfish
```

### Step Six: Cleanup

Kill the proxy running in the background...


### Updating the Docker images

