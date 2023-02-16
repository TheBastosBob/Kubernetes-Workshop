# Kubernetes-Workshop

## Step 0 - Install the tools

### Install Docker

You can use these commands: 
```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```
If you need more information, you can check the [official documentation](https://docs.docker.com/install/linux/docker-ce/ubuntu/).

### Install Minikube
Minikube is the tool that will allow you to run a Kubernetes cluster on your computer. You can use these commands:
```bash
curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/
```
#### Add to the PATH:
```bash
sudo mkdir -p /usr/local/bin/
sudo install minikube /usr/local/bin/
```

If you need more information, you can check the [official documentation](https://kubernetes.io/docs/tasks/tools/install-minikube/).

### Install Kubectl
Kubectl is the tool that will allow you to manage your Kubernetes cluster
In fact kubect is already installed with minikube, so you just have to add it to the PATH:
```bash
sudo ln -s /usr/local/bin/minikube /usr/local/bin/kubectl
```

If you need more information, you can check the [official documentation](https://kubernetes.io/docs/tasks/tools/install-kubectl/).


## Step 1 - Run the cluster

### Useful commands:

#### Start the cluster
```bash
minikube start
```

#### Check the cluster
```bash
kubectl get nodes
```

#### Stop the cluster
```bash
minikube stop
```

#### Delete the cluster
```bash
minikube delete
```

## Step 2 - Create a Pod

The pod is the smallest unit of deployment in Kubernetes. It is a group of containers that are deployed together.
this the base of the Kubernetes architecture.

lets create a pod with a simple http bin container:
```bash
kubectl run httpbin --image=kennethreitz/httpbin
```

### Useful commands:

#### Check the pod
```bash
kubectl get pods
```

#### Check the logs
```bash
kubectl logs httpbin
```

If you want to access the container, you can use the exec command:
```bash
kubectl exec -it httpbin -- /bin/bash
```

#### Delete the pod
```bash
kubectl delete pod httpbin
```

## Step 3 - Create a custom Pod

### Create your pod with the yaml file

We already created a yaml file for you, you just have to complete it.

You can try to run the httpbin image for example.

When you are done, you can create the pod with this command:
```bash
kubectl apply -f pod.yml
```


## Step 4 - Open the pod to the outside world (easy way)

It's cool your have a pod, but you can't access it from the outside world.

### Using the port-forward command

You can use the port-forward command to access your pod from the outside world.

```bash
kubectl port-forward <container_name> <port_on_your_computer>:<port_on_the_container>
```

For example, if you want to access the httpbin container on the port 80, you can use this command:
```bash
kubectl port-forward httpbin 8080:80
```

Now you can access the container on the port 8080 of your computer.

## Step 5 - The pods are better together

### Create a deployment

A deployment is a group of pods that are deployed together.

You can create a deployment with the yaml file.

you can find the doc [here](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/).

When you are done, you can create the deployment with this command:
```bash
kubectl apply -f deployment.yml
```

### Useful commands:

#### Check the deployment
```bash
kubectl get deployments
```

#### Check the pods
```bash
kubectl get pods
```

#### Check the logs
```bash
kubectl logs <pod_name>
```

#### Delete the deployment
```bash
kubectl delete deployment <deployment_name>
```

## Step 6 - Persistent storage

The pods are better together, but they are not persistent by default.
When you delete a pod, the data is lost.
So you need to use a persistent storage to save your data.

### Create a persistent volume

A persistent volume is a storage that is not linked to a pod.

You can create a persistent volume with the yaml file.



## Step 8 - Open the deployment to the outside world (hard way)

### Create a service

A service is a group of pods that are deployed together.

If you are here you know how to create a deployment, so you can create a service with the yaml file.

you can find the doc [here](https://kubernetes.io/docs/concepts/services-networking/service/).

This tutorial can help you: https://kubernetes.io/docs/tutorials/stateless-application/expose-external-ip-address/



When you are done, you can create the service with this command:
```bash
kubectl apply -f service.yml
```








