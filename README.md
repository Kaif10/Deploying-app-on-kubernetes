# Deploying-app-on-kubernetes

Installation / Create Cluster
We already know how the Kubernetes clusters work, so it’s time to move to the tools that we’ll use.
Kubectl is a command-line interface for running commands which will be processed on Kubernetes clusters. With kubectl, you can deploy applications, check and manage cluster resources, view logs and much more.
Minikube creates and implements the environment of the Kubernetes physical cluster in your local environment.
VirtualBox is a cross-platform virtualization tool.

Let’s first check the version of minikube by typing minikube version command.
$ minikube version
minikube version: v1.3.1

Now we can create our cluster in a virtual machine - let’s do this by typing minikube start and minikube status.
$ minikube start
😄  minikube v1.3.1 on linux (amd64)
🔥  Creating virtualbox VM (CPUs=2, Memory=2048MB, Disk=20000MB) ...
🐳  Configuring environment for Kubernetes v1.15.2 on Docker 18.09.8
🚜  Pulling images ...
🚀  Launching Kubernetes ...
⌛  Verifying: apiserver proxy etcd scheduler controller dns
🏄  Done! kubectl is now configured to use "minikube"
$ minikube status
host: Running
kubelet: Running
apiserver: Running
kubectl: Correctly Configured: pointing to minikube-vm at 192.168.99.100

Let’s verify if our cluster works and if kubectl can communicate with cluster - and for that, we’ll use kubectl cluster-info command.
$ kubectl cluster-info
Kubernetes master is running at https://192.168.99.100:8443
KubeDNS is running at https://192.168.99.100:8443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

You can also connect to minikube virtual machine to see what processes are running on the node. To do this type minikube ssh on the command line.
Now we can check the list of available nodes on the cluster - let’s type kubectl get nodes in the terminal.
$ kubectl get nodes
NAME       STATUS   ROLES    AGE     VERSION
minikube   Ready    master   3m41s   v1.14.3

You can also use the kubectl describe node minikube command to check a more detailed description of the node.

Let’s label this node so we can improve nodes management later. Type kubectl label nodes minikube type=backend command.
$ kubectl label nodes minikube type=backend
node/minikube labeled

To verify that label is added correctly type kubectl get nodes --show-labels command. 
$ kubectl get nodes --show-labels
NAME     STATUS ROLES  AGE   VERSION  LABELS
minikube Ready  master 6m36s v1.14.3




 create a working directory, then inside of it add another directory named main and place the file hello.go into it. The directory structure should look like this:
<working directory>/main/hello.go
  
In the hello.go file, add the following code, which will allow us to run a simple server that we’ll use to test our deployment.
  
Now we can run our application - in the main directory type the following command go run hello.go to run our simple server. When you visit the browser at http://localhost:8080/api/hello, you should see “Hello World”. Now we know that our application works so we can go to the next step - packing the application into the Docker container.
  
Let’s now create a Docker image for our application. In the main directory add a file named Dockerfile.
<working directory>/main/Dockerfile














