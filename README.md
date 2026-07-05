# 🚀 Kubernetes Cluster Deployment using kubeadm

<div align="center">

![Kubernetes](https://img.shields.io/badge/Kubernetes-v1.29.15-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![Ubuntu](https://img.shields.io/badge/Ubuntu-22.04-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)
![Rocky Linux](https://img.shields.io/badge/Rocky%20Linux-9-10B981?style=for-the-badge&logo=rockylinux&logoColor=white)
![Containerd](https://img.shields.io/badge/Containerd-2.x-575757?style=for-the-badge&logo=containerd&logoColor=white)
![Calico](https://img.shields.io/badge/Calico-v3.30.2-F28C28?style=for-the-badge)
![VMware](https://img.shields.io/badge/VMware-Workstation-607078?style=for-the-badge)

</div>

---

# 📖 Project Overview

This project demonstrates the complete deployment of a **production-style Kubernetes cluster** using **kubeadm**.

The cluster consists of **one Ubuntu Control Plane** and **two Rocky Linux Worker Nodes**, all running inside **VMware Workstation** on a Host-Only virtual network.

Instead of using Minikube or Kind, the cluster was built manually to gain practical experience with Kubernetes administration, Linux system configuration, networking, container runtime management, and cluster troubleshooting.

Throughout this project, every Kubernetes component was configured manually, including:

- kubeadm
- kubelet
- kubectl
- containerd
- Calico CNI
- CoreDNS
- kube-proxy

Several real-world issues were encountered during deployment, such as:

- Disk Pressure on the Control Plane
- Filesystem expansion after increasing virtual disk size
- Missing `ip_forward`
- Incorrect DNS resolver path (`/run/systemd/resolve/resolv.conf`)
- Calico initialization failures
- Worker node bootstrap issues

Each problem was analyzed and resolved until the cluster reached a healthy production state.

---

# 🎯 Project Objectives

The main objectives of this project were:

- Deploy Kubernetes from scratch using kubeadm
- Build a Multi-Node Kubernetes Cluster
- Configure Containerd as the Container Runtime
- Deploy Calico Networking
- Configure CoreDNS
- Join Rocky Linux worker nodes
- Validate cluster communication
- Troubleshoot common Kubernetes deployment issues
- Document every deployment step

---

# 🖥️ Infrastructure

| Component | Details |
|-----------|---------|
| Virtualization | VMware Workstation |
| Cluster Type | Multi-Node |
| Control Plane | Ubuntu 22.04.5 LTS |
| Worker Nodes | Rocky Linux 9 |
| Kubernetes | v1.29.15 |
| Container Runtime | containerd 2.x |
| CNI Plugin | Calico v3.30.2 |
| DNS | CoreDNS |
| Cluster Bootstrap | kubeadm |
| Network Type | Host-Only Network |

---

# 🌐 Cluster Topology

| Hostname | Role | Operating System | Internal IP |
|----------|------|------------------|-------------|
| master | Control Plane | Ubuntu 22.04 | 192.168.75.129 |
| node1 | Worker Node | Rocky Linux 9 | 192.168.75.146 |
| node2 | Worker Node | Rocky Linux 9 | 192.168.75.147 |

---

# 🏗️ Cluster Architecture

<p align="center">

<img src="screenshots/architecture.png" width="1000">

</p>

The architecture above illustrates the complete Kubernetes cluster built during this project, including:

- Ubuntu Control Plane
- Two Rocky Linux Worker Nodes
- Containerd Runtime
- kubeadm Bootstrap
- Calico Networking
- CoreDNS
- kube-proxy
- Host-Only VMware Network

---

# ⚙️ Technologies Used

| Technology | Purpose |
|------------|----------|
| Ubuntu Server 22.04 | Kubernetes Control Plane |
| Rocky Linux 9 | Worker Nodes |
| Kubernetes | Container Orchestration |
| kubeadm | Cluster Bootstrap |
| kubelet | Node Agent |
| kubectl | Cluster Administration |
| containerd | Container Runtime |
| Calico | Pod Networking |
| CoreDNS | Cluster DNS |
| kube-proxy | Service Networking |
| VMware Workstation | Virtualization Platform |

---

# 📁 Project Structure

```
Create-kubeadm-cluster/
│
├── README.md
│
└── screenshots/
    ├── architecture.png
    ├── 01-cluster-overview.png
    ├── 02-master-node.png
    ├── 03-node1-status.png
    ├── 04-node1-services.png
    ├── 05-node1-network.png
    ├── 06-node2-status.png
    ├── 07-node2-services.png
    └── 08-node2-network.png
```

---

# 🌐 Network Configuration

The Kubernetes cluster was deployed inside a **VMware Host-Only Network**, allowing secure communication between all virtual machines without exposing the cluster externally.

| Network Component | Value |
|-------------------|-------|
| Network Type | VMware Host-Only |
| Network Address | 192.168.75.0/24 |
| Kubernetes API Server | 192.168.75.129:6443 |
| Pod Network | Calico |
| Pod CIDR | 172.16.0.0/16 |
| Service CIDR | 10.96.0.0/12 |

---

# 🖥️ Virtual Machines

## Control Plane

| Property | Value |
|----------|-------|
| Hostname | master |
| Operating System | Ubuntu Server 22.04.5 LTS |
| Kubernetes Version | v1.29.15 |
| Runtime | containerd |
| IP Address | 192.168.75.129 |

Responsible for:

- Kubernetes API Server
- Scheduler
- Controller Manager
- etcd
- Cluster Management

---

## Worker Node 1

| Property | Value |
|----------|-------|
| Hostname | node1 |
| Operating System | Rocky Linux 9 |
| Runtime | containerd |
| IP Address | 192.168.75.146 |

Responsible for:

- Running Application Pods
- kubelet
- kube-proxy
- Calico Node

---

## Worker Node 2

| Property | Value |
|----------|-------|
| Hostname | node2 |
| Operating System | Rocky Linux 9 |
| Runtime | containerd |
| IP Address | 192.168.75.147 |

Responsible for:

- Running Application Pods
- kubelet
- kube-proxy
- Calico Node

---

# ⚙️ Kubernetes Components

| Component | Description |
|-----------|-------------|
| kubeadm | Bootstrap and initialize the cluster |
| kubelet | Node Agent running on every machine |
| kubectl | Kubernetes CLI |
| containerd | Container Runtime Interface (CRI) |
| kube-proxy | Cluster networking and service routing |
| CoreDNS | Internal DNS resolution |
| Calico | Pod Networking (CNI) |
| etcd | Kubernetes Key-Value Store |
| kube-apiserver | Main Kubernetes API |
| kube-controller-manager | Cluster Controllers |
| kube-scheduler | Pod Scheduling |

---

# 📦 Software Versions

| Software | Version |
|-----------|----------|
| Kubernetes | v1.29.15 |
| kubeadm | v1.29.15 |
| kubelet | v1.29.15 |
| kubectl | v1.29.15 |
| containerd | 2.x |
| Calico | v3.30.2 |
| Ubuntu | 22.04.5 LTS |
| Rocky Linux | 9 |
| VMware Workstation | Latest |

---

# ✅ Cluster Features

✔ Multi-Node Kubernetes Cluster

✔ Manual kubeadm Installation

✔ Containerd Runtime

✔ Calico Networking

✔ CoreDNS

✔ kube-proxy

✔ Worker Nodes Successfully Joined

✔ Pod-to-Pod Communication

✔ Internal DNS Resolution

✔ Cluster Networking Validation

✔ Production-style Architecture

---

# 📋 Prerequisites

Before deploying the cluster, the following configurations were completed on all nodes.

### System Preparation

- Hostnames configured
- Static IP addresses assigned
- `/etc/hosts` configured
- Time synchronization verified

### Linux Configuration

- Swap disabled
- Required kernel modules loaded
- IP forwarding enabled
- Bridge networking enabled

### Container Runtime

- containerd installed
- SystemdCgroup enabled
- containerd service enabled
- CRI verified

### Kubernetes Packages

- kubeadm
- kubelet
- kubectl

---

# 🔧 Linux Kernel Configuration

The following kernel parameters were configured on every node.

```

net.bridge.bridge-nf-call-iptables = 1
net.bridge.bridge-nf-call-ip6tables = 1
net.ipv4.ip_forward = 1

```

Kernel modules loaded:

```

overlay
br_netfilter

```

These settings are required for Kubernetes networking and Calico CNI.

---

# 🚀 Deployment Workflow

The cluster was deployed manually using **kubeadm**, following Kubernetes best practices.

## Step 1 — Prepare All Nodes

On every machine:

- Update packages
- Disable swap
- Configure kernel modules
- Enable IP forwarding
- Install containerd
- Configure SystemdCgroup
- Install kubeadm, kubelet and kubectl
- Configure hostname and `/etc/hosts`

---

## Step 2 — Initialize the Control Plane

Initialize Kubernetes on the master node.

```

kubeadm init \
--pod-network-cidr=172.16.0.0/16

```

After initialization:

- Configure kubectl
- Verify API Server
- Generate Worker Join Command

---

## Step 3 — Install Calico CNI

Install Calico networking.

```

kubectl apply -f calico.yaml

```

Calico provides:

- Pod Networking
- Pod Routing
- Network Policies
- Cross-node Communication

---

## Step 4 — Join Worker Nodes

Execute the generated kubeadm join command on each worker node.

```

kubeadm join <MASTER_IP>:6443 \
--token <TOKEN> \
--discovery-token-ca-cert-hash sha256:<HASH>

```

After joining:

- kubelet registers the node
- kube-proxy starts
- Calico daemon starts
- Node becomes Ready

---

## Step 5 — Verify the Cluster

Verify cluster health.

```

kubectl get nodes

kubectl get pods -A

kubectl cluster-info

```

Expected Result

- All Nodes Ready
- CoreDNS Running
- Calico Running
- kube-proxy Running

---

# 📊 Cluster Validation

The following checks were performed after deployment.

| Validation | Status |
|------------|--------|
| Master Ready | ✅ |
| Worker 1 Ready | ✅ |
| Worker 2 Ready | ✅ |
| CoreDNS Running | ✅ |
| Calico Running | ✅ |
| kube-proxy Running | ✅ |
| API Server Reachable | ✅ |
| Pod Networking Working | ✅ |
| DNS Resolution Working | ✅ |

---

# 📸 Deployment Screenshots

## 🏗️ Cluster Architecture

<p align="center">
 <img width="1536" height="1024" alt="digrame" src="https://github.com/user-attachments/assets/d7eedf37-4139-481d-bed0-0ba2d5732198" />


</p>

---

## 🌐 Cluster Status

Shows the overall cluster status including all nodes, Kubernetes version, and system pods.

<p align="center">
 <img width="1677" height="527" alt="1" src="https://github.com/user-attachments/assets/0765d414-6dd0-40e8-b19a-3a1b728bfc47" />

</p>

---

# 🖥️ Worker Node 1

### 📌 Node Information

Hostname and IP address of Worker Node 1.

<p align="center">
 <img width="1677" height="527" alt="2" src="https://github.com/user-attachments/assets/f7d5dadf-f878-4e74-a653-99559f5d7d70" />

</p>

### 📌 Kubernetes Services

Verifies that **containerd** and **kubelet** services are running correctly.

<p align="center">
  <img width="1670" height="521" alt="3" src="https://github.com/user-attachments/assets/052e1597-5422-4949-aa69-b474e222d5da" />

</p>

### 📌 Network Configuration

Shows the hosts file, kernel modules, and IP forwarding configuration.

<p align="center">
  <img width="1053" height="145" alt="4" src="https://github.com/user-attachments/assets/4be2b4d4-7cc9-412a-a60f-e96d18dee573" />

</p>

---

# 🖥️ Worker Node 2

### 📌 Node Information

Hostname and IP address of Worker Node 2.

<p align="center">
  <img width="1662" height="601" alt="6" src="https://github.com/user-attachments/assets/4e709cf4-7847-4930-991a-e8b6acc1b010" />

</p>

### 📌 Kubernetes Services

Verifies that **containerd** and **kubelet** services are running correctly.

<p align="center">
 <img width="1667" height="275" alt="7" src="https://github.com/user-attachments/assets/f94e48d5-046f-49f9-9aba-b333b6a6a476" />

</p>

### 📌 Network Configuration

Shows the hosts file, kernel modules, and IP forwarding configuration.

<p align="center">
  <img width="1547" height="247" alt="8" src="https://github.com/user-attachments/assets/d5e1ca98-e233-4aaf-9ae4-b7ec50c7b4e7" />

</p>

---

## ✅ Deployment Verification

The screenshots confirm that:

- All three nodes successfully joined the Kubernetes cluster.
- The Control Plane is running on Ubuntu 22.04.
- Worker Node 1 and Worker Node 2 are running Rocky Linux 9.
- Calico CNI is deployed successfully.
- CoreDNS is running correctly.
- containerd is configured as the container runtime.
- kubelet service is active on all worker nodes.
- Required networking configuration (br_netfilter and ip_forward) is enabled.
- All nodes reached the **Ready** state.


---

# 🔍 Troubleshooting

During deployment several issues were encountered and successfully resolved.

## Disk Pressure on Control Plane

**Problem**

```
NodeHasDiskPressure
```

**Solution**

- Increased VM Disk Size
- Extended Linux Partition
- Resized Filesystem
- Verified Available Storage

---

## Worker Node Join Failure

**Problem**

```
ip_forward = 0
```

**Solution**

Enabled:

```
net.ipv4.ip_forward=1
```

Applied using:

```
sysctl --system
```

---

## Calico Init Failure

**Problem**

```
Failed to create pod sandbox
```

**Cause**

Incorrect resolver configuration.

**Solution**

Updated kubelet configuration:

```
resolvConf: /etc/resolv.conf
```

Restarted kubelet.

---

## CNI Plugin Not Initialized

**Problem**

```
NetworkPluginNotReady
```

**Solution**

Verified:

- containerd
- kubelet
- Calico Images
- Network Configuration

After restarting services, all nodes became Ready.

---

# 🎯 Result

The deployment resulted in a fully operational Kubernetes cluster with:

- One Ubuntu Control Plane
- Two Rocky Linux Worker Nodes
- Calico CNI
- CoreDNS
- kube-proxy
- containerd Runtime

The cluster is healthy and ready for deploying containerized workloads.

---

# 📚 References

- Kubernetes Documentation
- kubeadm Documentation
- Calico Documentation
- containerd Documentation

---

# 👨‍💻 Author

**Mohamed Mosad**

Computer & Software Engineer

GitHub:
https://github.com/Mohamed-Mosad-98

LinkedIn:
https://www.linkedin.com/in/mohamed-mosad-516aa717b/

---

⭐ If you found this project helpful, consider giving the repository a Star.
