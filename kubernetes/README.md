# Kubernetes Pod

We are moving from Docker to Kubernetes.

In Docker we are building a container and we are deploying a container.  
In Kubernetes also we use this container that we have to deploy in Docker. Because at the end of the day it is Kubernetes or Docker. The end goal is deployment of application in a container.

So the concept of containerization…  
What Kubernetes says is don’t deploy application and container as is, but deploy it as a Pod.

---

Now why we can’t deploy a container directly?  
Why we should deploy a container as a Pod in Kubernetes?  
Why we should not deploy directly as a container in Kubernetes?

A basic Pod is described as a definition of how to run a container.

In Docker, to run a container we have a command called docker run, and we pass arguments like detached mode, port, network, name, and volume as parameters. All the arguments run the container by writing commands.

Whereas in Kubernetes, these specifications are passed in a Pod element. This is basically a concept that is similar to containerization but abstracts the user defined command in the Pod specification element.

---

In Kubernetes, instead of a container we deploy a Pod.  
A Pod contains a single container or it can even contain multiple containers.

If you build a Pod with one single container, it is exactly like a Docker container. The only difference is instead of using a command like docker run and passing the arguments, you will use a YAML file. In the YAML file all the specification details of the container will be there. Pod YAML is an enterprise level declaration capability for standardization.

---

Now assume you have an application deployed in a container and this wants to read some config files or user related files from another container. Instead of creating two different Pods, you can put two containers in a single Pod.  

If multiple containers are in a single Pod, they have some advantages:

- Share storage  
- Share network  
- Share communication  

If container 1 wants to talk to container 2, they can directly access each other. Or if both of them want to share some files, because they are in the same Pod, they can share files. This is usually a rare case, but it is a practice when containers need to be closely connected.

---

Kubernetes allocates the cluster IP address to the Pod.  
You can access the application in the container using the Pod cluster IP address.  

Pod is a wrapper that Kubernetes has created for the container to make life easier for developers.  
IP addresses are generated for the Pods, not for the containers.

---

In production systems we deal with hundreds or thousands of containers. We have a wrapper like a Pod which is defined in the YAML file. For example, if a developer goes to a Git repo and looks for a Pod definition, it contains everything. The application is running inside, it has a volume mount, and it has networking and multiple other details.  

For developers, Kubernetes has created a wrapper for the container.

When you are dealing with a Pod you will deal with a single container or access the container using the cluster IP address. kube-proxy is generating the IP address.

---

In Docker we have a command to run a container.  
In Kubernetes we have *kubectl*. It is a command line tool for Kubernetes. It can directly interact with a Kubernetes cluster.  

Examples:  
```bash
kubectl get nodes
kubectl get pods
kubectl get deployments
