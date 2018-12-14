![Logo](https://github.com/KishanRavindran/Kubernetes/blob/master/GeppettoIcon.png?raw=true"Logo")

# Nexus on Kubernetes
   In here we will see on how to deploy nexus with kubernetes with volumes for data backup.

# Content
1. [Prerequisites](#prerequisites)
1. [Nexus Installtion](#nexus-installation)

# Prerequisites
 [Install minikube](https://kubernetes.io/docs/tasks/tools/install-minikube/)<br/>
 [Install VM](https://www.virtualbox.org/wiki/Downloads)
 
# Nexus Installation<br/>
   Nexus  is a repository manager. It allows you to proxy, collect, and manage your dependencies so that you are not constantly juggling a collection of JARs. It makes it easy to distribute your software. Internally, you configure your build to publish artifacts to Nexus and they then become available to other developers.<br/> 
   
### Setting up Nexus<br/>
 Before we start you need to start the minikube once you have installed it.
 
      minikube start
      
  After that you check whether it didn't error out by checking the status.
  
      minikube status
      
  You will see the below line if the minikube is running successfully.
  
      minikube: Running
      cluster: Running
      kubectl: Correctly Configured: pointing to minikube-vm at 192.168.99.100
   
 In here i am going to deploy the nexus in kubernetes with just a Deployment file and Service file. You will think what is Deployment file and service file and what is usage of them. 
 
  The Deployment file is nothing but a kind in the Kubernetes where the Kind deployment is used for the Deployment controller which provides declarative updates for Pods and ReplicaSets.You describe a desired state in a Deployment object, and the Deployment controller changes the actual state to the desired state at a controlled rate. You can define Deployments to create new ReplicaSets, or to remove existing Deployments and adopt all their resources with new Deployments.
  
  The Service file is where which helps the Pods to find way to keep track of the Pods inside the cluster. The Service is an abstraction which defines a logical set of Pods and a policy by which to access them - sometimes called a micro-service.
  
  For connecting the nexus in kubernetes we need to create two files. Here i am going to create them as [Deployment](https://github.com/KishanRavindran/Kubernetes/blob/master/docs/Deployment.yaml) and [Service](https://github.com/KishanRavindran/Kubernetes/blob/master/docs/Service.yaml) files. 
  
 Once you have created them as above you need to open the terminal give the following command to implement Deployment file by
 
         kubectl create -f Deployment.yaml
         
  after that is done you can check whether the deployment api has been successfully created is by giving 
  
         Kubectl get deployment
         
  When you give this command you will be able to see below content
  
      NAME          DESIRED   CURRENT   UP-TO-DATE   AVAILABLE   AGE
      nexus         1         1         1            1           20h
      
  The name refers to the Deployment name which you have mentioned in the Deployment.yaml file.
  
  
 Once that is done you will need to create the Service file by giving 
 
         kubectl create -f Service.yaml
         
  once you have created the service file you can check the status of that by
  
         kubectl get Service
         
      NAME              TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)          AGE
      nexus-service     NodePort    10.102.99.172    <none>        8081:32000/TCP   21h
  
  Once you have created the service and the deployment you need to check on the Pod which will has been created for this nexus-service.
  
  You check by giving 
  
         kubectl get pod
         
       NAME                           READY   STATUS    RESTARTS   AGE
      nexus-88dd9667f-djmt8          1/1     Running   1          21h

you see that pod is up and running.

You can also check the above contents in the minikube Dashboard itself by giving 

         minikube dashboard 
         
in the terminal which will one in the browser.

![UI](https://github.com/KishanRavindran/Kubernetes/blob/master/docs/Selection_077.png?raw=true"UI")

Deployment

![deploy](https://github.com/KishanRavindran/Kubernetes/blob/master/docs/Selection_078.png?raw=true"deploy")

Service

![Service](https://github.com/KishanRavindran/Kubernetes/blob/master/docs/Selection_079.png?raw=true"Service")

Pod

![Pod](https://github.com/KishanRavindran/Kubernetes/blob/master/docs/Selection_080.png?raw=true"Pod")

Once you have checked you need to open your nexus in the browser. For that you need to get the minikube IP address and the port number of the nexus from the service.

You can get the minikube IP address by giving 

      minikube ip
      
   which will show the Ip address 192.168.99.100 and from the service you need to get the port number which is
   
         kubectl get service nexus-service
         
        NAME            TYPE       CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
      nexus-service   NodePort   10.102.99.172   <none>        8081:32000/TCP   21h
      
  From the above content you need to take the port number 32000 and add it to the minikube ip. Once you have done that you will be open the nexus Repository in the browser.
  
  ![nexus](https://github.com/KishanRavindran/Kubernetes/blob/master/docs/Selection_081.png?raw=true"nexus")
  
  Once you have opened it you can login with the default username and password which is admin/admin123.After you can change the credentials for security purpose. 
