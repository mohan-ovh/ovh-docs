---
title: How to optimise the distribution of VMs on a host server
excerpt: How do you best distribute VMs on a host server to optimise resources?
legacy_guide_number: g1442
updated: 2018-03-26
---

## OVH PRO Configuration
PRO includes Dynamic Optimization to automatically distribute the load of a cluster among different host servers. 
OVH offers a default configuration of PRO:

![](images/img_1991.jpg){.thumbnail}
Dynamic Optimization executes every 20 minutes and automatically migrates VMs from one host server to another to match the settings shown on the image above.

## Exclude a VM from PRO
If you don't want a VM to be automatically migrated by PRO, you can exclude it by ticking the following box in the VM's settings:

![](images/img_1992.jpg){.thumbnail}

## Anti-affinity rules
In VMM, you can set up  on each VM, and you can specify if you don't want certain VMs on the same host server.

To do this, go to the VM's rules, and then "Hardware Configuration" > "Availability" > "Aa propertyvailability Sets":

![](images/img_1993.jpg){.thumbnail}
Create a rule and add it to "Assigned Properties":

![](images/img_1994.jpg){.thumbnail}
Do the same on the other VMs that you wish to separate.

