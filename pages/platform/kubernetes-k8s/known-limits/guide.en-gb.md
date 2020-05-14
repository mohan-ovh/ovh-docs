---
title: Known limits
excerpt: 'Requirements and limits to respect'
slug: known-limits
section: Technical resources
---


**Last updated March 26<sup>th</sup>, 2020.**

<style>
 pre {
     font-size: 14px;
 }
 pre.console {
   background-color: #300A24;
   color: #ccc;
   font-family: monospace;
   padding: 5px;
   margin-bottom: 5px;
 }
 pre.console code {
   border: solid 0px transparent;
   font-family: monospace !important;
   font-size: 0.75em;
   color: #ccc;
 }
 .small {
     font-size: 0.75em;
 }
</style>

## Nodes and pods

We have tested our OVHcloud Managed Kubernetes service with up to 100 nodes and 100 pods per node.  
While we are fairly sure it can go further, we advise you to keep under those limits.

In general, it's better to have several mid-size Kubernetes clusters than one monster-size one.

Delivering a fully managed service, including OS and other component updates, you will neither need nor be able to SSH as root into your nodes.

## LoadBalancer

We are currently offering OVHcloud Managed Kubernetes LoadBalancer service as a free preview, until the end of summer 2020.  
During the free preview there is a limit of 6 active `LoadBalancers` per cluster.  
This limit can be exceptionally raised upon request though our support team.  
There is also a limit of __10 open ports__ on every `LoadBalancer`, and these ports must be in a range between __1 and 49151__.

## OpenStack

Our Managed Kubernetes service is based on OpenStack, and your nodes and persistent volumes are built on it, using OVH Public Cloud. As such, you can see them in the `Compute` > `Instances` section of [OVH Public Cloud Manager](https://www.ovh.com/manager/public-cloud/). It doesn't mean that you can deal directly with these nodes and persistent volumes as other cloud instances.  

The *managed* part of OVHcloud Managed Kubernetes Service means that we have configured those nodes and volumes to be part of our Managed Kubernetes.  
Please refrain from manipulating them from the *OVH Public Cloud Manager* (modifying ports left opened, renaming, resizing volumes...), as you could break them.

There is also a limit of __20__ Managed Kubernetes Services by Openstack project (also named Openstack tenant).

### Node naming

Due to known limitations currently present in the `Kubelet` service, be careful to set __a unique name__ to all your Openstack instances running in your tenant __including__ your "Managed Kubernetes Service" nodes and the instances that your start directly on Openstack through manager or API.  

The usage of the __period (`.`)__ character is forbidden in node name. Please, prefer the __dash__ (`-`) character instead.

## Ports

In any case, there are some ports that you shouldn't block on your instances if you want to keep your OVHcloud Managed Kubernetes service running:

### Ports to open from public network (INPUT)

- TCP Port 22 (*ssh*): needed for nodes management by OVH
- TCP Port 10250 (*kubelet*): needed for [communication from apiserver to worker nodes](https://kubernetes.io/docs/concepts/architecture/master-node-communication/#apiserver-to-kubelet)
- TCP Ports from 30000 to 32767 (*NodePort* services port range): needed for [NodePort](https://kubernetes.io/docs/concepts/services-networking/service/#nodeport) and [LoadBalancer](https://kubernetes.io/docs/concepts/services-networking/service/#loadbalancer) services

### Ports to open from instances to public network (OUTPUT)

- TCP Port 8090 (*internal service*): needed for nodes management by OVH

### Ports to open from others worker nodes (INPUT/OUPUT)

- UDP Port 8472 (*flannel*): needed for communication between pods
- UDP Port 4789 (*kube-dns internal usage*): needed for DNS resolution between nodes

## Private Networks

Private networks (vRack) aren't yet supported in OVHcloud Managed Kubernetes.  
Please refrain from adding private networks to your working nodes instances.

## Cluster health

The command `kubectl get componentstatus` is reporting the scheduler, the controller manager and the etcd service as unhealthy. This is a limitation due to our implementation of the Kubernetes control plane as the endpoints needed to report the health of these components are not accesible.

## Persistent Volumes resizing

Kubernetes `Persistent Volume Claims` resizing only allows to __expand__ volumes, not to __decrease__ them.  
If you try to decrease the storage size, you will get a message like:

```bash
The PersistentVolumeClaim "mysql-pv-claim" is invalid: spec.resources.requests.storage: Forbidden: field can not be less than previous value
```

For more details, please refer to the [Resizing Persistent Volumes documentation](../resizing-persistent-volumes/) documentation.
