![Logo](https://github.com/KishanRavindran/Kubernetes/blob/master/GeppettoIcon.png?raw=true"Logo")

# Nexus on Kubernetes
   In here we will see on how to deploy nexus with kubernetes with volumes for data backup.

# Content
1. [Prerequisites](#prerequisites)
1. [Nexus Installtion](#nexus-installation)

# Prerequisites
 Install minikube(https://kubernetes.io/docs/tasks/tools/install-minikube/)<br/>
 Install VM (https://www.virtualbox.org/wiki/Downloads)
 
# Nexus Installation<br/>
   Nexus  is a repository manager. It allows you to proxy, collect, and manage your dependencies so that you are not constantly juggling a collection of JARs. It makes it easy to distribute your software. Internally, you configure your build to publish artifacts to Nexus and they then become available to other developers.<br/> 
   
### Setting up Nexus<br/>
 In here i am going to deploy the nexus in kubernetes with just a Deployment file and Service file. You will think what is Deployment file and service file and what is usage of them. 
 
  The Deployment file is nothing but a kind in the Kubernetes where the Kind deployment is used for the Deployment controller which provides declarative updates for Pods and ReplicaSets.You describe a desired state in a Deployment object, and the Deployment controller changes the actual state to the desired state at a controlled rate. You can define Deployments to create new ReplicaSets, or to remove existing Deployments and adopt all their resources with new Deployments.
  
  The Service file is where which helps the Pods to find way to keep track of the Pods inside the cluster. The Service is an abstraction which defines a logical set of Pods and a policy by which to access them - sometimes called a micro-service.
  
  For connecting the nexus in kubernetes we need to create two files. Here i am going to create them as Deployment(https://github.com/KishanRavindran/Kubernetes/blob/master/docs/Deployment.yaml) and Service() files.
  
  

