# Ansible Role

In order to automate deployment and configuration of nodes, we provide Ansible Role which is used to deploy binary to target virtual machines.

Role link: [https://github.com/digitalnativeinc/ansible-role-substrate-deployer](https://github.com/digitalnativeinc/ansible-role-substrate-deployer)

### Pre-requisites

* Ansible installed
* Experience with Ansible assumed in this article

### Setup

Additional information is available in the repository README.

#### Requirements

Add the following to the **requirements.yml** file.

```yaml
# check latest version in repository, setup/variables may change between releases
roles:
  - name: substrate_deployer
    src: https://github.com/digitalnativeinc/ansible-role-substrate-deployer.git
    version: 0.x.x
```

#### Install the role

```bash
ansible-galaxy install -r requirements.yml
```

#### Setup playbook

Full list of variables available in **README**.

{% code title="validator.yml" %}
```yaml
- hosts: <target-inventory>
  roles:
    - substrate_deployer
  vars:
    substrate_node_version: latest
    substrate_node_validator: true
    substrate_node_logging: file
    substrate_node_friendly_name: Standard Validator
```
{% endcode %}

#### Run playbook

For help with command use `ansible-playbook --help`.

