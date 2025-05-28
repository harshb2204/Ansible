# How Ansible Works?

Ansible is an open-source automation tool used for configuration management, application deployment, and task automation. It works by connecting to your nodes and pushing out small programs, called "Ansible modules," to them. Here are the main components:

## 1. Inventory
The inventory is a list of hosts (servers or devices) that Ansible manages. It can be a simple text file with hostnames or IP addresses, or a more dynamic source.

## 2. Playbook
A playbook is a YAML file where you define the automation tasks you want to perform on your inventory. Playbooks describe the desired state of your systems and the steps to achieve it.

## 3. Module
Modules are reusable, standalone scripts that Ansible runs on your behalf. They perform specific tasks, such as installing packages, copying files, or managing services.

These components work together to automate IT processes efficiently and reliably.
We can add multiple modules in a playbook
Make directory
Install apache
Start webserver