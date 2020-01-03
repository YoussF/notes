## Kubernetes

Kubernetes (k8s) is an open-source system for automating deployments, scaling and management of conternerized applications. (kubernetes.io). It is the conductor of a container orchestra.

## Kubernetes Objects:
- [Pods](Pods.md)
- Deployments
- Namespaces
- ReplicationController (Manages Pods)
- StatefulSets
- DaemonSets
- Services
- ConfigMaps
- Volumes

## Some key features of k8s:

- Service Discovery / Load Balancing.
- Storage Orchestration.
- Automate Rollouts/Rollbacks.
- Self-healing.
- Secrets and Config Management.
- Horizontal scaling.

## Advantages of kubernetes:

- Package up ann app and let something manage it for us
- Not worry about management of the containers
- Eliminate single point of failure
- Scale Containers
- Update containers without bringing down the application
- Have a robust networking and persistent storage options

## Key Kubernetes Benefits

- **Orchestrate Containers** Needed for production
- **Zero-Downtime Deployments** Being able to deployment new versions of the app without service interruption.
- **Self Healing Capability** If one or more containers goes down, it will bring up the appropriate amount of new containers.
- **Scale Containers** We can change the state of the cluster to add more pods with a simple command.

## Developer Use Cases
- **Emulate production Environment Localy** Devs can easily replicate productions environment on there local machines
- **Move from Docker Compose to Kubernetes** Docker-compose doesn't have all the features of Kubernetes (pods, containers, deployments, replicaSets, Services, etc...). Kubernetes is the best way to go for production.
- **Creating an end-to-end testing environment** For use with  testing tools like Selenium or Cypress.io
- **Ensure application scales properly** Make sure that the app will still work properly after scaling. It's one thing to assume it will work, it's another to validate that.
- **Ensure secrets/config are working properly**
- **Performance testing scenarios** We might wan to see what are the limits of our application in a k8s cluster.
- **Workload scenarios (CI/CD and more)** We can use k8s for the build servers
- **Learn how to leverage deployment options** Canary test, AB or blue-green testing
- **Help DevOps resource and solve problems**

## Kubernetes Objects
- **POD** The POD is the smallest object in K8s. It consists of 1 or more containers.
- **Services** You can label your PODs and create a Service in K8s that will work as an internal load balancer between your PODs. Instead of pointing to the POD directly, you point to the service.
- **Replication Controllers** Now that we have our PODs behind a Service, it’s time for us to handle scaling PODs. We will use Replication Controllers for that.
- **Deployments** Another way of handling scaling PODs is via the Deployment Object. This is a special kind of object. Using this type of replication, you also have rolling updates of the POD container versions out-of-the-box. This is what we will use for our own application below.
Every time the application code changes, a new version of your application container will be built, and then we are going to update our Deployment manifest with the new version and tell K8s to apply the changes.
- **StatefulSets** StatefulSet is the workload API object used to manage stateful applications.
Manages the deployment and scaling of a set of Pods, and provides guarantees about the ordering and uniqueness of these Pods.
Like a Deployment, a StatefulSet manages Pods that are based on an identical container spec. Unlike a Deployment, a StatefulSet maintains a sticky identity for each of their Pods. These pods are created from the same spec, but are not interchangeable: each has a persistent identifier that it maintains across any rescheduling.
- **Volumes** On-disk files in a Container are ephemeral, which presents some problems for non-trivial applications when running in Containers. First, when a Container crashes, kubelet will restart it, but the files will be lost - the Container starts with a clean state. Second, when running Containers together in a Pod it is often necessary to share files between those Containers. The Kubernetes Volume abstraction solves both of these problems.
- **PersistentVolume** A PersistentVolume (PV) is a piece of storage in the cluster that has been provisioned by an administrator or dynamically provisioned using Storage Classes. It is a resource in the cluster just like a node is a cluster resource. PVs are volume plugins like Volumes, but have a lifecycle independent of any individual Pod that uses the PV. This API object captures the details of the implementation of the storage, be that NFS, iSCSI, or a cloud-provider-specific storage system.
- **PersistentVolumeClaim** A PersistentVolumeClaim (PVC) is a request for storage by a user. It is similar to a Pod. Pods consume node resources and PVCs consume PV resources. Pods can request specific levels of resources (CPU and Memory). Claims can request specific size and access modes (e.g., they can be mounted once read/write or many times read-only).
While PersistentVolumeClaims allow a user to consume abstract storage resources, it is common that users need PersistentVolumes with varying properties, such as performance, for different problems. Cluster administrators need to be able to offer a variety of PersistentVolumes that differ in more ways than just size and access modes, without exposing users to the details of how those volumes are implemented. For these needs, there is the StorageClass resource

## Some Kubectl commands
```bash
# Check k8s version
kubectl version
# View cluster information
kubectl cluster-info
# Retrieve information about k8s Pods, Deployments, Services, and more
kubectl get all
# Simple way to create a deployement for a Pod
kubectl run [container-name] --image=[image-name]
# Forward a port to allow external access
kubectl port-forward [pod] [ports]
# Expose a port for a Deployment/Pod
kubectl expose ...
# Create a resource
kubectl create [resource]
# Create or modify a resource
kubectl apply [resource]
#
watch kubectl get all -o wide
```

## WEB UI Dashboard
1. Go to [https://kubernetes.io/service-account-token](https://kubernetes.io/service-account-token) and copy the token.
2. Open terminal :
```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0-beta8/aio/deploy/recommended.yaml
kubectl describe secret -n kube-system
kubectl proxy
kubectl edit
kubectl patch
```
3. Visit the ddashboard URL and login using the token

## Quick Links
[Minikube](https://github.com/kubernetes/minikube)
[Docker Desktop](https://www.docker.com/products/docker-desktop)
[Kubernetes in Docker (Kind)](https://kind.sigs.k8s.io)
[Kubeadm](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm)
