# Running Kubernetes Locally
Minikube is a tool that makes it easy to run Kubernetes locally. Minikube runs a single-node Kubernetes cluster inside a VM on your laptop for users looking to try out Kubernetes or develop with it day-to-day.

## Before you begin
VT-x or AMD-v virtualization must be enabled in your computer’s BIOS.

## Requirements
* [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
* [Kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)

### Install VirtualBox
Install the correct package for your system from the following link: https://www.virtualbox.org/wiki/Downloads

### Install Kubectl
Kubectl is the Kubernetes command-line tool to deploy and manage applications on Kubernetes. Using kubectl, you can inspect cluster resources; create, delete, and update components; and look at your new cluster and bring up example apps.

```
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin/kubectl
kubectl version --client
```

## Installing Minikube
Install minikube on your machine running the following command:
```
curl -Lo minikube https://storage.googleapis.com/minikube/releases/v0.28.0/minikube-linux-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/
```
Verify the installation by running:
```
minikube version
```
You should see something like this:
```
minikube version: vX.XX.X
```
### Starting Minikube
To start your local kubernetes you need to run `minikube start`. Depending on your machine's specs this can take some time to complete. A successful output should look something like this:
```
Starting local Kubernetes v1.10.0 cluster...
Starting VM...
Downloading Minikube ISO
 153.08 MB / 153.08 MB [============================================] 100.00% 0s
Getting VM IP address...
Moving files into cluster...
Setting up certs...
Connecting to cluster...
Setting up kubeconfig...
Starting cluster components...
Kubectl is now configured to use the cluster.
Loading cached images from config file.
```
You may wish to launch the minikube VM with custom resource allocation, for that simply specify the number of cores and memory you want to assign to it like this:
```
minikube start --cpus 4 --memory 4096
```
Confirm your cluster is up by running `minikube status`
```
minikube: Running
cluster: Running
kubectl: Correctly Configured: pointing to minikube-vm at 192.168.99.100
```
You can also try `kubectl cluster-info`
```
Kubernetes master is running at https://192.168.99.100:8443
KubeDNS is running at https://192.168.99.100:8443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.
```

### Stopping Minikube
Run `minikube stop` to stop your local kubernetes cluster.
```
Stopping local Kubernetes cluster...
Machine stopped.
```

### Delete Minikube VM
To completely delete the minikube VM run `minikube delete`

## Next steps
Now that you've completed this introduction please continue to the [Exercises section](exercises/README.md).
