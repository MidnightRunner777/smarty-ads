# Ansible Playbook for Setting Up iptables Rules

## Overview

This playbook configures iptables rules on your target servers to manage SSH access control, monitoring ports, and application-specific ports. It allows traffic on specified ports from known IP addresses and rejects all other traffic directed to these ports.

## Requirements

- Ansible 2.9 or later.
- SSH access to the target servers.
- The target servers are listed in your Ansible inventory under `test-dev`.

## How to Run the Playbook

Ensure that your current working directory is where your playbook and inventory files are located.

1. **Set Up Your Inventory**

   If you haven't already, create an inventory file (e.g., `inventory/dev`) or update an existing one to include your target servers under the `test-dev` group.

2. **Configure Variables**

   Edit the `vars/monitoring.yml`, `vars/ssh.yml`, and `vars/app.yml` files to define the `monitoring_ips`, `ssh_protect`, and `app_protect` variables with the IP addresses allowed to access the respective ports.

3. **Run the Playbook**

   Use the following command to run the playbook with your inventory:

   ```bash
   ansible-playbook -i inventory/dev.yml iptables.yml
