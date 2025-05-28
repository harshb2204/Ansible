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
