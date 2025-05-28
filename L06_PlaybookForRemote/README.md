- Add the ip of your remote machine in the hosts file , in ungrouped
- to confirm it has been added run ansible-inventory --list

## SSH Configuration for EC2 Instance

### Problem: "Permission denied (publickey)" Error
When running:
```bash
ansible 3.110.78.252 -m ping
```
You might receive a "Permission denied (publickey)" error. This occurs when Ansible cannot authenticate with the EC2 instance due to:
- Wrong username (ansible_user)
- Missing or incorrect private key (ansible_ssh_private_key_file)
- Wrong path to the .pem key file

### Solution

1. **Identify the correct username** for your EC2 instance:
   - For Ubuntu: `ubuntu`
   - For Amazon Linux: `ec2-user`
   - For CentOS: `centos`

2. **Configure your inventory file** (`/etc/ansible/hosts`):
   ```
   3.110.78.252 ansible_user=ubuntu ansible_ssh_private_key_file=/home/harsh/harsh.pem
   ```

3. **Set correct permissions** for your key file:
   ```bash
   chmod 400 /home/harsh/harsh.pem
   ```

### Testing the Connection
Run:
```bash
ansible 3.110.78.252 -m ping
```

Expected result:
```
3.110.78.252 | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
```

- to use the initial yaml file to test connection we can just add all instead of localhost in the hosts part of the file or add the group.
- should give ok status

## Nginx Installation Playbook

Here's a sample playbook to install and configure Nginx on your remote hosts:

```yaml
---
- name: Install and start the service
  hosts: all
  become: yes

  tasks:
    - name: Installing nginx
      apt:
        name: nginx
        state: present
    - name: Starting the nginx service
      service:
        name: nginx
        state: started
        enabled: true
```



This playbook will:
1. Install Nginx using apt package manager
2. Start the Nginx service
3. Enable Nginx to start automatically on system boot

## Important Note About Privilege Escalation

When installing packages using apt, you need root privileges. If you encounter an error like:

```
Installing packages via apt requires root privileges.
Your playbook runs as user ubuntu (non-root).
The apt module tries to run apt-get install nginx, but fails because it's not running as root.
```

To fix this, make sure your playbook includes `become: yes` at the play level (as shown in the example above) or at the task level. This tells Ansible to use sudo when running commands that require root privileges.


