# CSR1000v Deployment Tool

Ansible playbook to deploy a single or multiple CSR1000v's
from a template on ESXi through Vmware vCenter.

There are two playbooks in this tooling. One to deploy
CSR1000v's from the inventory file and one to undeploy them.


* [Requirement](#requirements)
* [Setup](#setup)
* [Usage](#usage)
* [Contributing](#contributing)

## Requirements

This role requires the vmware_guest module and Ansible 2.8.

## Setup

The "deploy-vm-template" role contains common bootstrap properties for each CSR1000v.
Each CSR1000v is bootstrapped using vApp properties. In this example each CSR1000v
is bootstrapped for programmability training. NETCONF, RESTCONF, and SSH are bootstrapped
along with a user/pass of cisco/cisco.

### Inventory

Look inside the example inventory file and update parameters as appropriate. The parameters in
the inventory file are unique variables for each router.
Configurable parameters include:

*`hostname`*\
*`deploy_vsphere_datastore`*\
*`guest_notes`*\
*`inventory_ip`*

### Role Variables

The "deploy-vm-template" and the "destroy-vm" role accept various variables including:

#### Vmware vCenter Environment

*`deploy_vsphere_host`*\
*`deploy_vsphere_user`*\
*`deploy_vsphere_password`*\
*`deploy_vsphere_datacenter`*\
*`deploy_vsphere_folder`*

#### CSR1000v Common Configuration

*`guest_memory`*\
*`guest_vcpu`*\
*`guest_disk`*\
*`guest_template`*\
*`router_gateway`*\
*`port_group1`*\
*`port_group2`*\
*`port_group3`*

These variables can be found and modified in var.yml.

## Usage

Deploy all routers in inventory
```
ansible-playbook -i inventory deploy-pods.yml
```

Deploy subset of routers in inventory
```
ansible-playbook -i inventory deploy-pods.yml --limit student-routers
```

Undeploy routers
```
ansible-playbook -i inventory undeploy-pods.yml
```

## Contributing
See [CONTRIBUTING](./CONTRIBUTING.md)
