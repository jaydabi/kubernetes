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

# examples

Instead of using the playbook like shown below, you can also adapt the playbook. Check [Ansible documentation](https://docs.ansible.com/ansible/latest/user_guide/playbooks.html).

## installing docker and kubernetes

Either install a single node

    ansible-playbook playbook.yml -i server1, --tag install

or a bunch of nodes.

    ansible-playbook playbook.yml -i server1,server3,192.168.99.88 --tag install
    
## setting up a master node

Instead of using the masters ip for kubernetes api queries, you should think about using a load balancer like suggested in the kubernetes documentation. This is especially relevent for multi-master clusters. Single node-clusters for development don't need this.

    ansible-playbook playbook.yml -i server1 --tag init_kubernetes_master --extra-vars "control_plane_endpoint=server1.tld node_name=whatever-node-name"

The control plane could also be a DNS name.
