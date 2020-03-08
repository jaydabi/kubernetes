# kubernetes
Ansible role for docker &amp; kubernetes on a Debian host

# available tags

* `install`

  Will install docker and kubernetes. Do this to bootstrap all nodes.

* `init_kubernetes_master`

  Will initialize a kubernetes master. Only use when initially setting up a cluster.

* `generate_kubernetes_join_command`

  Run against master. Will copy a join command to local machine. Use join_kubernetes_cluster afterwards to join nodes to your kubernetes cluster.

* `join_kubernetes_cluster`

  Will use join command created by generate_kubernetes_join_command to join an existing kubernetes cluster.

* `init_single_node_cluster`

  May be used after init_kubernetes_master to create a single node cluster. 
