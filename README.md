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
