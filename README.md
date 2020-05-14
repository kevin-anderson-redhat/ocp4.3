# auto-config
Ansible automation to perform post cluster deployment configuration

## Post Cluster Deployment Configuration
The cluster.yml playbook is used to configure a new OCP 4.3+ cluster to include:
* infrastructure nodes with dedicated workloads
* cluster-logging
* Default new project Network Policies

An inventory for the cluster must exist before these configurations can be
automatically applied.

## Usage
```
ansible-playbook -i ocp409.yml cluster.yml
```
