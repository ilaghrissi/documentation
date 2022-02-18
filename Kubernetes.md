# Kubernetes

### 1- namespace 

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