# SUSE Linux cluster manager ansible config

Create a basic cluster manager node for deploying SUSE linux to nodes in the cluster.

The cluster consists of head node and a set of cluster nodes that provide a service.
The head node is dual homed to an external and cluster network.  The external network reachable from the ansible client.  The cluster network is 
shared by the head node and a number of cluster nodes.  The head node uses the cluster network
to boot and provision the remaining nodes.
The cluster nodes may be attached to additional
networks depending on the service provided by the cluster, for example an IB network or other dedicated data network.

The current playbook is designed to initalize a basic dhcp and tftp boot environment to bring the cluster nodes online with a base OS configured
to support cluster operation and management, e.g. a cluster wide admin account.

Other tooling can be used at this point to futher image the cluster for the services it is intended to provide.