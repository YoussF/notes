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
# Delete a Pod using YAML file that created it
kubectl delete -f pod.yml
```

## Defining a Pod with YAML
Write pod.yml file
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
Then
```bash
# To perform a 'trial' create and also validate the YAML
kubectl create -f pod.yml --dry-run --validate=true
# Create a Pod from YAML
# Will throw an error if Pod already exists
kubectl create -f pod.yml
# Alternate way to create update a Pod from YAML
kubectl apply -f pod.yml
# Use --save-config  when you wan to use kubectl apply in the future
kubectl create -f pod.yml --save-config
```

## Get information about a running pod
```bash
kubectl get pod my-nginx -o YAML
kubectl describe pod my-nginx
```

# Get an interactive shell from a Pod
```bash
kubectl exec my-nginx -it sh
```

# Edit pod configuration file
```bash
kubectl edit -f pod.yml
```

# Pod Health
Kubernetes relies on something called Probes to determine the health of a Pod container.
A Probe is a diagnostic performed periodically by the kubelet on a container. Since the developers
knows the most about the code running in that container,they write the Probe that is appropriate
for that Pod in the YAML file.
There are two type of Probes :
- **Liveness Probe** can be used to determine is a pod is healthy and running as expected.
- **Readiness Probe** can be used to determine if a Pod should receive requests.

Failed Pod containers are recreated by default (restartPolicy defaults to Always)
Here are some exmaples of what a Probe can do:
- **ExecAction** Executes an action inside the container. (if returned 0 than it is successful)
- **TCPSocketAction** Perform a TCP check against the container's IP address on a specified port.
- **HTTPGetAction** Perform a HTTP GET request against container

Probes can have the following results:
- Success
- Failure
- Unknown

### Defining an HTTP Liveness Probe
```bash
apiVersion: v1
kind: Pod
...
spec:
  containers:
  - name: my-nginx
    image: nginx:alpine
    livenessProbe:
      httpGet:
        path: /index.html
        port: 80
      initialDelaySeconds: 15
      timeoutSeconds: 2
      periodSeconds: 5
      failureThreshold: 1
```
### Defining an ExecAction Liveness Probe
```yaml
apiVersion: v1
kind: Pod
...
spec:
  containers:
  - name: liveness
  image: k8s.gcr.io/busybox
  args:
  - /bin/sh
  - -c
  - touch /tmp/healthy; sleep 30;
    rm -rf /tmp/healthy; sleep 600
  livenessProbe:
    exec:
      command:
      - cat
      - /tmp/healthy
    initialDelaySeconds: 5
    periodSeconds: 5
```
### Defining a Readiness Probe
```yaml
apiVersion: v1
kind: Pod
...
spec:
  containers:
    - name: my-nginx
    image: nginx:alpine
    readinessProbe:
      httpGet:
        path: /index.html
        port: 80
      initialDelaySeconds: 2
      periodSeconds: 5
```
