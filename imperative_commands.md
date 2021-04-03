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

### Delete pod mypod

<details><summary>show</summary>
<p>

```bash
kubectl delete pod mypod
```

</p>
</details>

### Get pod yaml file without actually running a pod

<details><summary>show</summary>
<p>

```bash
kubectl run mypod --image=nginx --dry-run=client -o yaml > pod.yaml
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