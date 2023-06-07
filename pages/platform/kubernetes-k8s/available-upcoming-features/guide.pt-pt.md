---
title: Available and planned features
excerpt: ''
routes:
    canonical: '/pages/platform/kubernetes-k8s/available-upcoming-features'
updated: 2022-08-11
---

**Last updated August 11th, 2022.**

We list here the most frequently requested OVHcloud Managed Kubernetes features that are currently available or planned in the upcoming year.

### Available features

- **Persistent Volumes**: Use the integrated Cinder Volumes to host the persistent data of your stateful containerized workloads. Details in the [working with persistent volumes](/pages/platform/kubernetes-k8s/persistent-volumes-on-ovh-managed-kubernetes) guide.
- **Load Balancer**: Use the integrated External Load Balancers to expose your services on any port of a dedicated public IPv4. Details available in the [exposing your services](/pages/platform/kubernetes-k8s/using-lb) guide.
- **Private Network**: Deploy your Kubernetes in an OVHcloud Public Cloud private network to consume and expose applications on our multiregion and multiproduct private network (vRack). Note : You can still leverage integrated External Load Balancers to expose some services on a public Internet IPv4.
- **New versions**: We support the last 3 stable K8s versions and offer the latest one during the quarter following its official release. We also propose managed version upgrades.
- **RBAC and APIserver IP restrictions**: Use the standard [RBAC authorization](https://kubernetes.io/docs/reference/access-authn-authz/rbac/){.external} mode to distribute rights within your organization and/or assure compatibility with specific applications. You can additionaly choose to restrict access to your Kubernetes APIserver to a selection of IPv4 ranges.
- **Pod autoscaling**: Use the [standard horizontal pod autoscaler](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/){.external} to distribute dynamically your containerized workloads on a given set of worker nodes.
- **Node pools management**: Easily [resize you cluster through our UI or directly using standard Kubernetes tooling by editing a Nodepool CRD ](/pages/platform/kubernetes-k8s/node-pools-crd) .
- **Location choice**: We offer Managed Kubernetes service in all OVHcloud Public Cloud regions as of June 2022. OVHcloud customers (excluding customers of OVHcloud US) can use the service in France (GRA and SBG), Canada (BHS), Poland (WAW), UK, Germany (DE) and APAC (SYD and SYN). OVHcloud US customers can use the service in 2 US regions.

### Planned features

We now expose the roadmap of this service, as all of our Public Cloud services, publicly in the OVHcloud GitHub repo.
When visiting [the "containers and orchestration" board of the roadmap](https://github.com/ovh/public-cloud-roadmap/projects/1) you can view all the backlog, vote or subscribe to notifications on features and even propose new ones to be considered.

## Go further

- If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](https://www.ovhcloud.com/pt/professional-services/) to get a quote and ask our Professional Services experts for assisting you on your specific use case of your project.

- Join our community of users on <https://community.ovh.com/en/>.

