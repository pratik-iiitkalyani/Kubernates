# Topic
Setup Kubernetes Cluster on CentOS 7

# Prerequisites
  - Swap should be disabled
  - Disable swap
  
  ```
  sed -i '/swap/d' /etc/fstab
  swapoff -a
  ```
  
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

# Install Kubernetes packages
In order to grab latest package for Kubernetes, we need to configure our yum repository

```
sudo bash -c 'cat <<EOF > /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-x86_64
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
exclude=kube*
EOF'
```

Disable SELinux to prevent any communication issues on all the nodes

```
sudo setenforce 0
sudo sed -i 's/^SELINUX=enforcing$/SELINUX=permissive/' /etc/selinux/config
```

```
sudo yum install -y kubelet kubeadm kubectl --disableexcludes=kubernetes
```

After the installation is completed, enable kubelet as a service.

```
sudo systemctl enable kubelet && sudo systemctl start kubelet
```



