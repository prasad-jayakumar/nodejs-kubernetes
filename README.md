# Steps for running dockerised node js app in kubernetes

1. Install Minikube and kubectl using https://kubernetes.io/docs/tasks/tools/

2.  $ minikube version
    $ kubectl version

3. Start the minikube in your machine
    $ minikube start

This command will spin up the cluster, having one node that serves as a worker and one as a master node.


4. Define YAML File To Create A Deployment In Kubernetes Cluster - Deploy.yaml

5. $ kubectl create -f deploy.yaml

Kubectl is Kubernetes client which is used to create objects. With kubectl create, you can create any object -f indicates we’re using a file and deploy.yaml is the file that will be used to create an object.

6. Expose the deployment to internet

    $ kubectl expose deployment nodejs-deployment --type=LoadBalancer --port=3000

    In another window, start the tunnel to create a routable IP for the 'nodejs-deployment' deployment:

    $ minikube tunnel

    To find the routable IP, run this command and examine the EXTERNAL-IP column

    $ kubectl get services nodejs-deployment

    Your deployment is now available at EXTERNAL-IP:3000










