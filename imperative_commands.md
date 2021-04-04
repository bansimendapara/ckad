### List all pods

<details><summary>show</summary>
<p>

```bash
kubectl get pods
kubectl get po
```

</p>
</details>

### Get details of nginx pod

<details><summary>show</summary>
<p>

```bash
kubectl describe pod nginx
```

</p>
</details>

### List all pods in the current namespace, with more details

<details><summary>show</summary>
<p>

```bash
kubectl get pods -o wide
kubectl get po -o wide
```

</p>
</details>

### List all pods in mynamespace

<details><summary>show</summary>
<p>

```bash
kubectl get pods --namespace=mynamespace
kubectl get pods -n mynamespace
```

</p>
</details>

### List all pods in all namespaces

<details><summary>show</summary>
<p>

```bash
kubectl get pods --all-namespaces
kubectl get pods -A
```

</p>
</details>

### Get a pod's YAML

<details><summary>show</summary>
<p>

```bash
kubectl get pod mypod -o yaml
```

</p>
</details>

### Get the image used to create the pod

<details><summary>show</summary>
<p>

```bash
kubectl describe pod mypod | grep -i image
```

</p>
</details>

### Create pod nginx with image nginx:alpine

<details><summary>show</summary>
<p>

```bash
kubectl run nginx --image=nginx:alpine
```

</p>
</details>

### Create pod nginx with image nginx:alpine in mynamespace

<details><summary>show</summary>
<p>

```bash
kubectl run nginx --image=nginx:alpine -n mynamespace
```

</p>
</details>

### Delete pod, replica set, deployment

<details><summary>show</summary>
<p>

```bash
kubectl delete pod mypod
kubectl delete rs myreplica
kubectl delete deploy mydeploy
```

</p>
</details>

### Create pod with labels

<details><summary>show</summary>
<p>

```bash
kubectl run nginx --image=nginx:alpine -l tier=frontend,env=dev
```

</p>
</details>

### Get pod or deployment yaml file without actually running a pod

<details><summary>show</summary>
<p>

```bash
kubectl run mypod --image=nginx --dry-run=client -o yaml > pod.yaml
kubectl create deploy webapp --image=nginx --replicas=4 --dry-run=client - o yaml > webapp.yaml
```

</p>
</details>

### Edit pod

<details><summary>show</summary>
<p>

```bash
kubectl edit pod mypod
```

</p>
</details>

### Create kubernetes resources using yaml file

<details><summary>show</summary>
<p>

```bash
kubectl create -f file.yaml
kubectl apply -f file.yaml
```

</p>
</details>

### List all replication controller, replica sets and deployments

<details><summary>show</summary>
<p>

```bash
kubectl get rc
kubectl get rs
kubectl get deploy
```

</p>
</details>

### List all resources available in all namespaces (Pods, Replication Controllers, Replica Sets, Deployments, Services)

<details><summary>show</summary>
<p>

```bash
kubectl get all -A
```

</p>
</details>

### Get details of replication controller, replica sets and deployments

<details><summary>show</summary>
<p>

```bash
kubectl describe rc myrc
kubectl describe rs myrs
kubectl describe deploy mydeploy
```

</p>
</details>

### Show lables for all pods

<details><summary>show</summary>
<p>

```bash
kubectl get pods --show-lables
```

</p>
</details>

### Replace a resource by filename

<details><summary>show</summary>
<p>

```bash
kubectl replace -f pod.yaml
```

</p>
</details>

### Scale deployment, replica set or replication controller

<details><summary>show</summary>
<p>

```bash
kubectl scale --replicas=3 -f my-replica.yaml
kubectl scale --replicas=3 rs my-replicas
```

</p>
</details>

### Create deployment

<details><summary>show</summary>
<p>

```bash
kubectl create deploy webapp --image=nginx --replicas=4
```

</p>
</details>

### Create service of type ClusterIP to expose pod redis on port 6379

<details><summary>show</summary>
<p>

```bash
kubectl expose pod redis --name=redis-service --port=6379
```
This will automatically use the pod's labels as selectors.

```bash
kubectl create service clusterip redis --tcp=6379:6379
```
This will not use the pod's labels as selectors but, it will assume selectors as app=redis.

</p>
</details>

### Create service of type NodePort to expose pod or deployment 80 on port 30080 on the nodes:

<details><summary>show</summary>
<p>

```bash
kubectl expose pod nginx --name=nginx-service --type=NodePort --port=80 --dry-run=client -o yaml > nginx.yaml
kubectl expose deploy webapp --name=webapp-service --type=NodePort --port=80 --dry-run=client -o yaml > webapp.yaml
```
This will automatically use the pod's labels as selectors, but you cannot specify the node port. You have to generate a definition file and then add the node port in manually before creating the service with the pod.

```bash
kubectl create service nodeport nginx --tcp=80:80 --node-port=30080
```
This will not use the pod's labels as selectors. To do that, you need to get yaml file and manually edit it.

</p>
</details>