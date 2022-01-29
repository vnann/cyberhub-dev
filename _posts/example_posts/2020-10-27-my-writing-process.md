---
title: Kubernetes and Containers Learning Guide
date: 2020-10-27
author: Naveen Nannapaneni
toc: true
layout: post
avatar: assets/img/favicon.ico
tags:
  - Kubernetes
  - Container
category: k8s
---

## Table of Content <!-- omit in toc -->

- [Resources](#resources)
- [NetApp Kubernetes and Containers learning Guide](#netapp-kubernetes-and-containers-learning-guide)
- [What is Kubernetes?](#what-is-kubernetes)
- [How to install Kubernets](#how-to-install-kubernets)
- [Kubernets commands](#kubernets-commands)
  - [Kubernets Run, Create, and Apply](#kubernets-run-create-and-apply)
    - [<font color=red> ***NOTE:***</font>](#font-colorred-notefont)
  - [Pods & Controllers](#pods--controllers)
  - [First Pod with kubectl run](#first-pod-with-kubectl-run)
    - [Create Pods with kubectl](#create-pods-with-kubectl)
  - [Scaling ReplicaSets](#scaling-replicasets)
  - [Get container logs](#get-container-logs)
    - [Get a bunch of details about an object, including events!](#get-a-bunch-of-details-about-an-object-including-events)
    - [Describe](#describe)
- [Podman](#podman)
- [Linux Namespaces with Container](#linux-namespaces-with-container)
- [NetApp Triednt: Storage Persistence for Containers](#netapp-triednt-storage-persistence-for-containers)
  - [Why are Enterprises Moving to Containerized Apps?](#why-are-enterprises-moving-to-containerized-apps)
  - [A Kubernetes Cluster](#a-kubernetes-cluster)
  - [NetApp Trident](#netapp-trident)
    - [Storage Class (SC)](#storage-class-sc)
  - [Persistent Volume Claims (PVC)](#persistent-volume-claims-pvc)
  - [Persistent Volume (PV)](#persistent-volume-pv)
- [Trident](#trident)
  - [NetApp's Container Storage Provisioner](#netapps-container-storage-provisioner)
  - [High-Level Architectural Diagram](#high-level-architectural-diagram)
  - [Preserving Trident's Own State](#preserving-tridents-own-state)
  - [Trident Install](#trident-install)
  - [Storage provisioning and Deprovisioning with Trident](#storage-provisioning-and-deprovisioning-with-trident)
  - [Managing Persistence for Stateful Applications Made Easy](#managing-persistence-for-stateful-applications-made-easy)
  - [PVC Cloning Makes for a Easy Accurate Testing Environment](#pvc-cloning-makes-for-a-easy-accurate-testing-environment)
  - [Volume Import](#volume-import)

## Resources 

1. [Generalist SE: Kubernetes and Containers Learning Guide](https://fieldportal.netapp.com/explore/results?k=ansible&popupstate=%7B%22state%22:%22app.viewContent%22,%22srefParams%22:%7B%22source%22:9,%22sourceType%22:null,%22assetId%22:909137,%22assetComponentId%22:911060%7D%7D)
[Specialist SE: Kubernetes and Containers Learning Guide](https://fieldportal.netapp.com/content/909176)
2. [K8S: Bootcamp Overview](https://fieldportal.netapp.com/explore/results?k=ansible&popupstate=%7B%22state%22:%22app.viewContent%22,%22srefParams%22:%7B%22source%22:9,%22sourceType%22:null,%22assetId%22:909137,%22assetComponentId%22:911060%7D%7D)
3. [Learn Kubernetes using Interactive Browser-Based labs - Katacoda](https://www.katacoda.com/courses/kubernetes)
4. [Kubernetes Bootcamp](https://kubernetesbootcamp.github.io/kubernetes-bootcamp/) 
5. [stern - Stern allows you to tail multiple pods on Kubernetes and multiple containers within the pod. Each result is color coded for quicker debugging.](https://github.com/wercker/stern)
6. [kubectl Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)
7. [kubectl for Docker Users](https://kubernetes.io/docs/reference/kubectl/docker-cli-to-kubectl/)
8. [Kubernetes on Vsphere (Packer - Part 1)](https://medium.com/kuranda-labs-engineering/kubernetes-on-vsphere-packer-part-1-b2ed5071e2b5)
9. [Kubernetes on Vsphere (Terraform - Part 2)[https://medium.com/kuranda-labs-engineering/kubernetes-on-vsphere-terraform-part-2-64bac93116e9]
10. [Learn Kubernetes Basics](https://kubernetes.io/docs/tutorials/kubernetes-basics/)

## NetApp Kubernetes and Containers learning Guide

1. [Generalist SE: Kubernetes and Containers Learning Guide](https://fieldportal.netapp.com/content/884295?searchbar=%7B%22ord%22:3,%22k%22:%22Trident%22%7D&popupstate=%7B%22state%22:%22app.viewContent%22,%22srefParams%22:%7B%22source%22:9,%22sourceType%22:null,%22assetId%22:909137,%22assetComponentId%22:911060%7D%7D)
2. [Specialist SE: Kubernetes and Containers Learning Guide](https://fieldportal.netapp.com/content/884295?searchbar=%7B%22ord%22:3,%22k%22:%22Trident%22%7D&popupstate=%7B%22state%22:%22app.viewContent%22,%22srefParams%22:%7B%22source%22:9,%22sourceType%22:null,%22assetId%22:909176,%22assetComponentId%22:911099%7D%7D)

**Container Basics**
1. Understanding Docker architecture
2. Able to run docker commands to list, modify, delete, and run containers
3. Able to create a simple dockerfile
4. Able to use environment variables in dockerfiles
5. Able to use docker compose
6. Understand the basic architecture of Kubernetes – master, workers
7. Able to deploy an app in a Kubernetes cluster
8. Understand the role NetApp Trident plays in Docker and Kubernetes
10. Able to describe the value of NetApp Kubernetes Service

**DevOps/Container NetApp Communities**
1. [Cloud Native Application Deployment](https://www.youtube.com/watch?v=cVDg7tgzIQc&feature=youtu.be)
2. [Data protection for container deployments **NetApp slide deck**](https://netapp.sharepoint.com/:p:/s/TechnologieForumSharing/Ea__RziXOfZOu4M2SlJ-wagB2YgVKwrn2lPNIV5qX6I4DA?e=DeIr7u)
3. [NetApp Container Storage Integration for Trident/Kubernetes (CSI Trident)](https://netapp-trident.readthedocs.io/en/stable-v19.04/kubernetes/trident-csi.html?highlight=csi)
4. [ONTAP/CVO on Kubermatics](https://docs.kubermatic.io/concepts/architecture/)
5. [Container Backup on Kubernetes](https://github.com/kubernetes-csi/external-snapshotter)
6. [github container storage interface](https://github.com/container-storage-interface/spec/blob/master/spec.md.)
7. [NKS ALM](https://www.youtube.com/watch?v=Nl2ktdr4GSo&feature=youtu.be)
8. [Kubernetes the Hard Way](https://github.com/kelseyhightower/kubernetes-the-hard-way)
9. [NetApp Trident: Storage Persistence for Container](https://www.netapp.com/us/forms/live-events/devops-master-class-webcast/netapp-trident-storage-persistence-containers.aspx)

## What is Kubernetes?

- Kubernetes is designed as highly available cluster of computers that are connected to work as a single unit ([kubernetes.io](https://kubernetes.io/docs/tutorials/kubernetes-basics/))
- Kubernetes role is to automate the distribution (scheduling) of application containers across a cluster in an efficient way.
- Kubernetes cluster contains 
  - ***Master*** is coordinationg the cluster 
  - ***Nodes*** are where we run applications 
    - Its is a VM or a physical computer that is used as a worke machine in a kubernetes cluster.

## How to install Kubernets
```sh
  sudo apt-get update
  sudo apt-get upgrade
  sudo apt-get install -y apt-transport-https
  sudo apt install docker.io
  sudo systemctl start docker
  sudo systemctl enable docker
  sudo apt-get install curl
  sudo curl -s https://packages.cloud.google.com/apt/doc/apt-key.pgp | sudo apt-key add
  sudo curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add
  sudo chmod 777 /etc/apt/sources.list.d
  vi kubernetes.list
  mv kubernetes.list /etc/apt/sources.list.d/
  suod apt-get update
  sudo apt-get update
  sudo vi /etc/apt/sources.list.d/kubernetes.list
  sudo apt-get update
  cat /etc/apt/sources.list.d/kubernetes.list
  sudo apt-get install -y kubelet kubeadm kubectl kubernetes-cni
  sudo swapoff -a
  sudo kubeadm init
  mkdir -p $HOME/.kube
  sudo kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml
  sudo kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/k8s-manifests/kube-flannel-rbac.yml
  sudo kubectl get pods --all-namespaces
  sudo kubectl get nodes
  sudo kubectl run --image=nginx nginx-app --port=80 --env="DOMAIN=clusters"
  sudo kubectl expose deployment nginx-app --port=80 --name=nginx-http
  sudo kubectl expose pod nginx-app --port=80 --name=nginx-http
  sudo docker ps -a
```
## Kubernets commands
1. [Browser based kubernetes cluster training](https://www.katacoda.com/courses/kubernetes/launch-single-node-cluster)
**Start kubernets cluster on Ubuntu 18.04**
```sh
minikube version
minikube start --wait=false
```

**Cluster Info**

```sh
kubectl cluster-info

Kubernetes master is running at https://172.17.0.77:8443
KubeDNS is running at https://172.17.0.77:8443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

kubectl get nodes
```

### Kubernets Run, Create, and Apply

| command        | notes                                            |
|----------------|--------------------------------------------------|
| kubectl run    | changing to be only for pod creation * in 1.18 * only create single pods.|
| kubectl create | create some resources via CLI or YAML            |
| kubectl apply  | Create / Update anything via YMAL                |
| kubectl version | version display [client version and server version |

**<font color=red> NOTE:</font>**

- kubectl run nginx --image nginx created a Deployment named nginx before 1.18 (which creates a ReplicaSet, which creates a Pod)
- kubectl run nginx --image nginx creates a Pod named nginx in 1.18+
- Creating a Deployment in 1.18: kubectl create deployment nginx --image nginx

### Pods & Controllers

- Pods --> ReplicaSet --> Deployment

### First Pod with kubectl run

#### Create Pods with kubectl
  - Two ways to deploy Pods (containers) - Via commands, or via YAML
  - kubectl run [name of the pod/container] --image [image of the app]
  ```
    kubectl run my-nginx --image nginx 
    kubectl get pods
    kubectl get all
   ```
  - To delete the pod which will delete the replicaset and pods within it.
  ```
    kubectl delete deployment my-nginx
  ```

### Scaling ReplicaSets

- Start a new deployment for one replica/pod
- ```
    kubectl run my-apache --image httpd
    kubectl get all 
  ```
- Scale it up with another pod
- ```
  kubectl scale deploy/my-apache --replicas 2
  kubectl scale deployment my-apache --replicas 2
  kubectl get pods
  ```

### Get container logs

```
  kubectl logs deployment/my-apache
  kubectl logs deployment/my-apache --follow --tail 1
```

#### Get a bunch of details about an object, including events!

- It will pull logs from all the pods which has same tags. for example: my-apache 
```
  kubectl logs -l run=my-apache
```

#### Describe

```
  kubectl get pods
  kubectl describe [name of the pod]
```

## Podman 
1. [Podman - The next generation of Linux container tools](https://developers.redhat.com/articles/podman-next-generation-linux-container-tools/)

## Linux Namespaces with Container 
1. [Isolate containers with a user namespace](https://docs.docker.com/engine/security/userns-remap/)

## NetApp Triednt: Storage Persistence for Containers

### Why are Enterprises Moving to Containerized Apps?

- Standardized packaging (support micr0services)
- Run on any OS
- Update and launch apps faster
- Consistent with DevOps methods
- Lightweight (support more containers than VMs)
- Containers are generally ephemeral (howerver, needd data persistence)
- They are more efficiennt than VMs (Since VM need more resources)

### A Kubernetes Cluster

- **Master nodes** are responsible for administration and maintaining cluster state
  - etcd, kube-api, controllers, etc.
- **Worker nodes** are responsible for deploying and running applicaiton pods
  - pods contain one or more containers that share volume spaces, IP address, namespace
- **Infra nodes** are responsible for deploying and running pods used for infrastructure purposes
  - E.g. ha-proxy, metrics, logging, etc. used by openshift. (not part of Kubernetes upstream)

### NetApp Trident

#### Storage Class (SC)

- Describes a storage offering and associates a provisioner
- Parameters are used to provide additional informatoion to the provisioner
- Parameters are opaque to Kubernetes
- PVCs specify storage classes, storage classess specify provisioners, and provisioners map storage classes to PVs
- Storage Classess can also be used with statically provisioned PVs
- Typically configured by an administrator
  
```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadat:
  name: bronze
provisioner: netapp.io/trident
parameters:
  backendType: "ontap-nas"
  mediaType: "hdd"
  storagePools: "tenant1_nas:.*"
  provisioningType: "thin"
  snapshots: "true"
reclaimPolicy: "Retain"         --> This will control if the data need to be reainted when the container is removed.
```
### Persistent Volume Claims (PVC)

- Created by a user to request storage (Typically configured by a developer to ask for application storage )
- Specifies desired capacity and access mode, along with labels to aid with selection
- If available, kubernetes assigns a PV (Persistent Volume) to meet the requirements requested in the PVC
- Does not require an exact match for capacity

```yaml
Kind: PersistentVolumeClaim
apiVersion: v1
metadata:
  name: thepub
spec:
  accessModes: 
    - ReadWriteOnce
  resources:
    requests:
      storage: 5Gi
  storageClassName: bronze
```

### Persistent Volume (PV)

- Persistent storage introduced to Kubernetes by an administrator
  - Configured for backing storage device
- Abstracts the physical storage volume into consumable units for containers
  - Inludes connection information for the storage volume
  - Typically configured by an administrator or external provisioners like Trident.
  
```
apiVersion: v1
  kind: PersistentVolume
  metada:
    name: pv0003
  spec:
    capacity:
      storage: 5Gi
    accessModes:
      - ReadWriteMany
  storageClassName: bronze
    nfs:
      path: /tmp
      server: 172.17.0.2
```
## Trident

- Open Source Maintained and Supported by NetApp - Written in Go [Kubernets also written in Go]
- It is released in querterly with kubernets with one months later (ex: Kubernetes release 2020.03 Trident will be release 2020.04) 
- Version naming. Year.Month [eg. 2020.04]
- Its a storage orchestrator and used kubernetes as a pod by itself and uses kubernetes to depoly itself [supported on NetApp storage ]
- Only need one instance of the Trident per Kubernetes cluster no matter how many backend you have. 
- Trident deploys as 1 replica Pod. This means kubernetes will make sure one instance is always available.
- Trident is just a control plane, once its   
- Trident listens to K8s API to create persistent volumes

### NetApp's Container Storage Provisioner

- A dynamic, automated storage provisioner for popular distributions of kubernetes
- Abstract stroage backends into pools of capabilities
  - Ability to differentiate storage
  - Admin-specifiable IOPS, compression, disk type, etc.
- Map storage requests to storge pools
  - Backends may have one or more storage pools
- Open source and fully supported

### High-Level Architectural Diagram

![Trident_High_Level_Architectural_Diagram](images/Trident_High_Level_Architectural_Diagram.png)

- Two Containters - Trident-Engine and etcd (database - holds information about trident own deployment  (present volumes, storage classes, and backend (meaning backed point to storage)))
- You will use tridentctl to create backend (which is a json file which as all the informaton need to connect to NetApp and create voluems)
- Container/ orchestration Supports 
  - Kubernets through k8s plugin
  - Docker plugin
  - CSI plugin [Its in early stages does not have all the features related to kubernetes and docker]
  - REST API 

### Preserving Trident's Own State

- etcd Key Value Store
  - Stores metadata about Trident-managed volumes, backedns, and storage classes
  - Deployed with a PV when used with Trident; used external etcd if desiderd 
  - Moving forward kubernetes will allow ather apps to store data in its etcd database
    - Custom Resource Definitions (CRD)
      - The k8s preferred way of introducing new resources
      - Obviates need for having storage backend admin credentials in etcd
      - k8s API server automatically services and handles storage for CRDs

### Trident Install

```
  kubectl get nodes
  wget https://github.com/NetApp/trident/releases/download/v19.04.0/trident-installer-19.04.0.tar.gz
  tar -xf trident-installer-19.04.0.tar.gz
  cd trident-installer-19.04.0
  cd sample-input
  cd ..
  cp sample-input/sample-ontap-nas.json setup/backend.json
  vi setup/backend.json     # update the creds 
  ./tridentctl install -dry-run -n trident
  ./tridentctl install -n trident # Install in its own namespace
  kubectl get pod -n trident -o wide
  ./tridentctl version -n trident
```

### Storage provisioning and Deprovisioning with Trident

![Trident_Storage_Pools_and_Characteristics](images/Trident_Storage_Pools_and_Characteristics.png)
![Trident_Storage_Provisioning](images/Trident_Storage_Provisioning.png)
![Trident_Storage_Deprovisioning](images/Trident_Storage_Deprovisioning.png)


### Managing Persistence for Stateful Applications Made Easy


### PVC Cloning Makes for a Easy Accurate Testing Environment

- Easily use real data for testing


### Volume Import

- 
- Migrate from monolithic applications to containerized without losing data
- Volume migration from one cluster to another
- Kubernetes re-build
- Data Managmeent Disaster Recovery
- Validate with real data
  