# Hands-On: Deploying a Web App to Kubernetes

To create Kubernetes files from our Docker-Compose we can use `kompose`, a Tool that helps us by translating the Compose YAML files into Kubernetes deployment and services YAML files.

We already did that for you, so you can find the YAML files for our deployment in the repository.

To deploy your app to your local Kubernetes cluster (we will use Minikube here), we can use the `deployment.yaml` file in the kubernetes folder to create the pods on our local cluster.

Please verify that Minikube is up and running using `minikube status`. You should see the following output:

```
minikube
type: Control Plane
host: Running
kubelet: Running
apiserver: Running
kubeconfig: Configured
```

Use `kubectl apply -f [filename]` to create the resources on your local cluster for the application. This should result in one deployment with two pods (app & db) and a service for each pod.

<div align="right">
   
   [Prev](04_intro-to-deployments.md) - [Next](06_automate-k8s.md)
</div>