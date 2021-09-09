# Hands-On: Deploying a Web App to Kubernetes

To create Kubernetes files from our docker-compose file we can use `kompose`, a Tool that helps us by translating the Compose YAML files into Kubernetes deployment and services YAML files.

We already did that for you, so you can find the YAML files for our deployment in the repository within the folder `k8s`. To deploy your app to your local Kubernetes cluster (we will use Minikube here), we can use those YAML files.

Please verify that Minikube is up and running using `minikube status`. You should see the following output:

```
minikube
type: Control Plane
host: Running
kubelet: Running
apiserver: Running
kubeconfig: Configured
```

Use `kubectl apply -f ./k8s` to create the resources on your local cluster for the application. This command applies the already created YAML files in the `k8s` folder and creates the resources accordingly. 
This should result in two deployments with two pods named `web` and `redis` and two services. 

When everything is created and the pods are running, go ahead and check if you can reach the application!

<div align="right">
   
   [Prev](04_intro-to-deployments.md) - [Next](06_intro-to-testing.md)
</div>
