Description  
===========

This is my OpenShift Repository for deploying an HA OpenShift Cluster

Usage
-----

SSH to Bastion Host in OpenShift Homework Lab v3.9:

`ssh -i ~/.ssh/id_rsa alexander.soul-computacenter.com@bastion.ad27.example.opentlc.com`  

`git clone https://github.com/soulmanos/openshift-homework.git`  

From Bash Shell:

`ansible-playbook ocp-deploy-main.yaml -i inventory`


### Installs:

```
INSTALLER STATUS *******************************************************
Initialization             : Complete (0:00:31)
Health Check               : Complete (0:01:35)
etcd Install               : Complete (0:01:09)
NFS Install                : Complete (0:00:15)
Load balancer Install      : Complete (0:00:20)
Master Install             : Complete (0:04:21)
Master Additional Install  : Complete (0:01:04)
Node Install               : Complete (0:06:11)
Hosted Install             : Complete (0:01:40)
Web Console Install        : Complete (0:00:32)
Metrics Install            : Complete (0:02:07)
Logging Install            : Complete (0:03:00)
Prometheus Install         : Complete (0:00:46)
Service Catalog Install    : Complete (0:01:39)
```