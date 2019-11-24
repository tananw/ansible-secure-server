# Ansible-playbook - securing server with hardened SSH and iptables

This Ansible playbook is used to create a new, non-root user with sudo access, as well as
upgrade installed packages and installing some new ones (vim and nmap), copy SSH public key
to allow logins without password and then to harden the SSH by disabling the root user and 
password authentication. It also installs and configures iptables to allow traffic only on 
ports 22, 80, 443 and icmp protocol.

## Usage

When the playbook is run for the first time, use this command while being in the project's directory: 
```bash
ansible-playbook provision.yml
```

When you run the playbook for the second time (and so on) be sure to follow instructions in comment in
file provision.yml, and run the playbook using:
```bash
ansible-playbook provision.yml
```

You can generate your own password with:
```bash
python3 -c 'import crypt; print(crypt.crypt("PASSWORD", crypt.mksalt(crypt.METHOD_SHA512)))'
```

Group of hosts 'webservers' is saved in the default location: /etc/ansible/hosts.