# Topic
Setup Kubernetes Cluster on CentOS 7

# Prerequisites
  - Swap should be disabled
  
# System updates
update our Linux system with all security patches or any other upgrades that will be ensure our system is up-to-date.
```
yum update -y
```
After system update, we are now ready to setup Kubernetes cluster. We will first setup docker and then setup Kubernetes

# Install and setup Master and Worker Nodes
Please ensure you have applied following steps to both master and worker node before moving on to steps specific to each nodes. Below steps are common for both master and worker nodes.

# Install and Setup Docker

```
yum install -y docker
```

Now we need to enable and start Docker as a service

```
sudo systemctl enable docker && sudo systemctl start docker
```
To verify if you have docker version 1.13 and higher, execute below command

```
sudo docker version
```



