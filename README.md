# Ansible_Essentials
Provides a framework for Ansible hosted with RHEL9 (5.14.0-570.23.1.el9_6.x86_64). <br/>Note, the majority of the playbooks are tailored for Alpine Linux (6.6.94-0-lts).

# Ansible_Directory
ansible.cfg  gather-facts.yml  idempotent.yml  inventory  test.yml  vcl.yml  webserverbk.yml  webserver.yml

# Ansible_Playbooks
gather-facts.yml - Provides an overview of each of the machines within the inventory.ini file
idempotent.yml - Displays the use of shell code (Hint: cat /tmp/hello.txt) [Note: This will always return - ok=1    changed=1]
test.yml - This is a simple playbook that writes a new file to the /tmp directory (Hint: cat /tmp/test.txt)
vcl.yml - This allows you to loop based on a conditional statement
webserverbk.yml - This allows for a webserver deployment for RHEL9
webserver.yml - This allows for a webserver deployment for Alpine Linux

# Ansible_Configuration
ansible.cfg - Use case displayed in this repository is host_key_checking = False (Hint: If DNS is not configured)
inventory - This is the .ini file that defines the hosts (accessible in Ansible) and the associated ssh logins and root escalation path(s) [Note: Not for PRODUCTION USE]

# Requirements
- Python3: pip install ansible (YUM and APK)
- sshpass: Alpine Linux (apk add)
- sudo: Alpine Linux (apk add)

# Useful_Commands
- Authenticated Playbook: ansible-playbook -i inventory -u ansible --ask-pass idempotent.yml
- Unauthenticated Playbook: ansible-playbook -i inventory vcl.yml
- Webserver Validation: curl http://172.18.117.179
- Alpine Linux: su - root (sudo command equivalent)
- Alpine Linux: echo '%wheel ALL=(ALL) ALL' > /etc/sudoers.d/wheel (Hint: Alter sudo group)
- Alpine Linux: chmod 0440 /etc/sudoers.d/wheel (Hint: Alter sudo group)
- Alpine Linux: sudo adduser ansible wheel
- RHEL9 Linux: sudo usermod -aG wheel ansible
