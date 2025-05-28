# First Basic Ansible Playbook

This is a simple Ansible playbook that tests connectivity to localhost using the `ping` module.

## Playbook Content

```yaml
---
- name: First basic playbook
  hosts: localhost

  tasks:
  - name: Test Connectivity
    ping:
```

## Explanation

- `name`: A descriptive name for the playbook
- `hosts: localhost`: Specifies that this playbook will run on the local machine
- `tasks`: Contains a list of tasks to be executed
- `ping`: A simple module that tests connectivity to the target host

## How to Run

To run this playbook, use the following command:

```bash
ansible-playbook playbook.yml
```

Make sure to save the playbook content in a file named `playbook.yml` in the same directory.
