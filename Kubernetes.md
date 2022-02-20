# Kubernetes

### 1.namespace 

### 2.pod

    kubectl get pods

### 3.service
to communicate between pods
if pod die the service will forward the request to another pod

### 4.ingress
to access to the application from the extern
route traffic into cluster

### 5.configMap
external configuration of the application like database url, or some url of services

### 6.secrets
like configMap but its store secret data like credentials in base64 encoded format

### 7.volumes
to store data it could be local storage (inside kubernetes cluster)
or remote (outside kubernetes cluster) it could be cloud  storage or external storage

### 8.deployment
to scale up or scale down the number of replicas of pods you need
deployment is for stateLess applications


### 9.statefulSet
to replicate database (because database has a state, and we can't replicate database as the application)

StatefulSet if of stateful applications

#### Kubernetes Architecture  

### 1. worker node

Every worker node should have two components : 
1. container runtime
2. kubelet
3. kube proxy

### 2. master node
1. Api Server : it's like  a cluster gateway. When you want to deploy application in kubernetes cluster you interact with Api server using some client (UI(kubernetes dashboard), Command line tool (kubelet), Kubernetes api) + it acts as gatekeeper for authentication (to make sure that only authenticated could interact with cluster and authorized request get through the cluster)
2. Scheduler : 
3. Controller manager : detect state changes like crashing pods
4. etcd : 

#### Create namespace 
Method 1 : 
create yml file namespace.yml : 
<pre>
apiVersion: v1
kind: Namespace
metadata:
   name: elk
</pre>
Run : 
<pre> kubectl create -f namespace.yml </pre>
<br/>
Method 2 : 
from json
<pre>
{
    "apiVersion": "v1",
    "kind": "Namespace",
    "metadata": {
    "name": "development",
    "labels": {
    "name": "development"
        }
    }
}
</pre>
Run : 
<pre>
kubectl create -f https://k8s.io/examples/admin/namespace-dev.json
</pre>

#### Show namespaces 
Show namespaces  : 
<pre> kubectl get namespaces </pre>
Results :
<pre>
NAME              STATUS   AGE
default           Active   30h
development       Active   5m34s
elk               Active   6m38s
kube-node-lease   Active   30h
kube-public       Active   30h
kube-system       Active   30h

</pre>

Show namespaces with labels :
<pre> kubectl get namespaces --show-labels </pre>
Results :
<pre>
NAME              STATUS   AGE     LABELS
default           Active   30h     kubernetes.io/metadata.name=default
development       Active   5m48s   kubernetes.io/metadata.name=development,name=development
elk               Active   6m52s   kubernetes.io/metadata.name=elk
kube-node-lease   Active   30h     kubernetes.io/metadata.name=kube-node-lease
kube-public       Active   30h     kubernetes.io/metadata.name=kube-public
kube-system       Active   30h     kubernetes.io/metadata.name=kube-system
</pre>


### 2- pods
Pod : is a collection of containers and its storage inside a node of kubernetes cluster
<br/>
we can create a : 
Pod with one container 
<br/>
Pod with multiple containers, for example keeping database container and data container in the same pod

<pre>
kubectl run "name of pod" --image="name of the image from registry"
</pre>

Example :
<pre>
kubectl run tomcat --image tomcat:8.0
</pre>



### Create Kubernetes Cluster in local machine
with : 
1. Minikube (https://kubernetes.io/docs/tasks/tools/)
2. MicroK8s (https://microk8s.io/)
3. k3s (https://k3s.io/)


### Taints and Tolerations