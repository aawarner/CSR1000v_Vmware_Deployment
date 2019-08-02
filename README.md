# CSR1000v Deployment Tool

Ansible playbook to deploy a single or multiple CSR1000v's
from a template on ESXi through Vmware vCenter.

There are two playbooks in this tooling. One to deploy the
CSR1000v's from the inventory file and one to undeploy them.

Each playbook has it's own associated role. The roles utilize
the "vmware_guest" Ansible module.

* [Setup](#setup)
* [Usage](#usage)
* [Contributing](#contributing)

## Setup

Modify var.yml with appropriate information to define Vmware
environment and CSR1000v common options. The "deploy-vm-template"
role contains common bootstrap properties for each CSR1000v. The CSR1000v
is bootstrapped using vApp properties. In this configuration each CSR1000v
is bootstrapped for programmability. NETCONF, RESTCONF, and SSH are bootstrapped
along with a user/pass of cisco/cisco.

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