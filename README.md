# SUSE Linux cluster manager ansible config

Create a basic cluster provisioning node for deploying SUSE linux to nodes in a cluster.
A cluster consists of head or management node and a set of cluster nodes that provide a service.

The provisioner is dual homed to an external and a provisioning network.  
The external network needs to be reachable from the ansible client to execute playbooks.
The provisioning network the pxe boot network for all cluster nodes.  The provisioners node uses the provisioning network to boot and provision the cluster nodes.
The cluster nodes may be attached to additional networks depending on the
service provided by the cluster, for example an hight bandwidth Ethernet or IB 
network or other dedicated data network.

The current playbooks are designed to initalize a basic dhcp and tftp boot environment 
on a provisioner node to bring the cluster nodes online with a base OS configured
to support cluster operation and management, e.g. with a cluster wide admin account.

Other tooling can be used at this point to futher image the cluster for the services it is intended to provide and is cluster dependent.

The groups_vars/all.example file shows settings that need to be defined.
There is a cluster dictionary that should be initialized to the nodes in the 
cluster and the node variables that support the needs of the ansible playbooks
and provisioning templates.  See the examples in that file.