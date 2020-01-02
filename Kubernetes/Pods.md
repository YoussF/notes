## Kubernetes Pod Core Concepts
A Pod is the basic execution unit of a k8s application, the smallest and simplest unit the k8s object model that you create or deploy. Here are some characteristics of a Kubernetes pod :

- Smallest object of the kubenetes object model.
- Environment for Containers.
- Organize application "parts" into pods (server, caching, APIs, database,etc,...)
- Pod IP, memory, volumes, etc, shared accross containers.
- Scale horizontally by adding Pods replicas.
- Pods live and die but never come back to life.

## Pods, IPs, and ports

- A pod within a node will have a cluster ip address
- Pod containers share the same network namespace (share IP/port)
- Pod containers have the same loopback network interface (localhost)
- Container process need to bind to different ports within a Pod.
- Ports can be reused by containers in sperate pods.

## Creating a Pod
The following command will create a deployment behind the scenes to run the pod on a cluster node. This approach is not recommanded since it is imperative
```bash
# Run the nginx:alpine container in a Pod
kubectl run [podname] --image=nginx:alpine
# List only Pods
kubectl get pods
# List all resources
kubectl get all
```

## Expose a Pod Port
Pods and containers are only accessible within the Kubernets cluser by default
One way to expose a container port externaly is to use:
```bash
# Enable Pod container to be called externaly
kubectl port-forward [name-of-pod] 8080:80
```

## Deleting a Pod
Running a Pod will case a deployment to be created
To delete a Pod use kubectl delete pod or find the deployment and use kubectl delete deployment
```bash
# Will cause pod to be recreated
kubectl delete pod [name-of-pod]
# Delete Deployment the manages the Pod
kubectl delete deployment [name-of-deployment]
```

## Defining a Pod with YAML
Here is a  simple YAML file that describe a very basic nginx pod
```yaml
apiVersion: v1            # Kubernetes API version
kind: Pod                 # Type of Kubernetes resource
metadata:                 # Metadata about the Pod
  name: my-nginx
spec:                     # The spec/blueprint for the pod
  containers:             # Information about the containers that will run in the Pod
  - name: my-nginx
    image: nginx:alpine
```
To perform a 'trial' create and also validate the YAML
````bash
kubectl create -f file.pod.yml --dry-run --validate=true
```
