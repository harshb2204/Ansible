---
- name: Install and start Nginx
  hosts: webservers  # Assuming 'webservers' is defined in your Ansible inventory
  become: true       # Tasks should be run with sudo privileges

  tasks:
    - name: Install Nginx
      apt:            # Using the apt module for package management on Debian/Ubuntu
        name: nginx   # Name of the package
        state: present # Ensure the package is installed
        update_cache: yes # Update the apt cache before installing

    - name: Start Nginx
      service:        # Using the service module to manage the service
        name: nginx
        state: started
        enabled: true # Ensure Nginx is enabled to start on boot
