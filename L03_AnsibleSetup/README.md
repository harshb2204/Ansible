# Ansible Setup Guide

## Overview
This guide covers the setup of Ansible using two virtual machines:
1. AWS EC2 instance
2. Local WSL (Windows Subsystem for Linux)

## Prerequisites
- AWS account with EC2 instance running Ubuntu
- WSL installed on your local machine
- SSH key pair for AWS EC2 access

## Setup Instructions

### 1. AWS EC2 Connection
Connect to your EC2 instance using SSH:
```bash
ssh -i ~/harsh.pem ubuntu@43.205.123.42
```

### 2. Ansible Installation
Follow the official Ansible installation guide for Ubuntu:
- Visit: https://docs.ansible.com/ansible/latest/installation_guide/installation_distros.html#installing-ansible-on-ubuntu
- Or use the following commands:
```bash
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt install ansible
```

### 3. Verification
Verify your Ansible installation by running:
```bash
ansible localhost -m ping
```
Expected output should show a successful "pong" response.

