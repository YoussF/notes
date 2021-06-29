## Ansible Running Playbook
```bash
# Run a playbook and execute all the tasks defined within it
ansible-playbook myplaybook.yml
# Overwrite the default hosts option in the playbook and limit execution to a certain group or host
ansible-playbook -l server1 myplaybook.yml
```
## Ansible oneline modules
```bash
# command module
ansible -i "rpi303," all -u vagrant -m command -a uptime
# shell module
ansible -i "rpi303," all -u vagrant -m shell -a "ps aux | grep vagrant | wc -l" --one-line
# raw module (no python)
ansible -i "rpi303," all -u vagrant -b -K -m raw -a "apt install -y git"
# apt module
ansible -i "rpi303," all -b -m apt -a 'name=nginx state=latest'
# service module
ansible -i "rpi303," all -b -m service -a 'name=nginx state=stopped'
# setup module
ansible -i "rpi303," all -m setup -a "filter=ansible_distribution*"
```

## Ansible config
```bash
# Show ansible config file location
ansible --version
# ansible.cfg example
[defaults]
inventory = ./inventory
remote_user = ansible
ask_pass = false
[privilege_escalation]
become = true
become_user = root
become_ask_pass = false
```
### Host-Based Connection Variables
```bash
project
├── ansible.cfg
├── host_vars
│ ├── server1.example.com # These settings override the ones in ansible.cfg
│ └── server2.example.com # These settings override the ones in ansible.cfg
└── inventory
# They also have slightly different syntax and naming
```
### Host-Based Connection and Privilege Escalation Variables
- **ansible_host**: specifies a different IP address or hostname to use for the connection for this host 
instead of the one in the inventory
- **ansible_port**: specifies the port to use for the SSH connection on this host
- **ansible_user**: specifies the user you want to use on this host
- **ansible_become**: specifies whether to use privilege escalation for this host
- **ansible_become_user**: specifies the user to become on this host
- **ansible_become_method**: specifies the privilege escalation method to use for this host 
### Preparation on the Managed Host
- One of the more common choices is to set up SSH key-based authentication to an unprivileged 
account that can use sudo to become root without a password
- The advantage of this is that you can use a specific account that only Ansible uses, and tie that to a 
particular SSH private key, but still have "passwordless" authentication
- Alternatively: SSH key-based authentication to the unprivileged account, then require the sudo
password for authentication to root
- Ansible allows you to select the mix of settings that works best for your security policy and stance

## Ansible inventory
```bash
# Verifiying inventory
ansible-inventory -y --list
# List all host in currnet inventory
ansible all --list-hosts
```

## Ansible Commands
- Ad hoc commands are simple, one line operations that are run without writing a playbook.
- They are useful for quick tests and changes.
- For example, to start a service or ensure a line exists in a file.
- Ad hoc commands have limitations.

## Ansible Modules
- Ansible provides modules, code that can be used to automate particular tasks
- Some uses of modules:
  - Ensure users exist with certain settings
  -  Make sure the latest version of a software package is installed
  - Deploy a configuration file to a server
  - Enable a network service and make sure that it is running
- Most modules are idempotent, which means they only make changes if a change is needed. 
Idempotent modules can be run safely multiple times.
- An ad hoc command runs one module on the specified managed host

```bash
# Getting documentation about module
ansible-doc ping
```

## Ansible Ad Hoc Commands
```bash
ansible host-pattern -m module [-a 'module arguments'] [-i inventory]
```
- The ansible command runs an ad hoc command
- Its host-pattern argument specifies the managed hosts to run on.
- Its -m option names the module that Ansible should run.
- Its -a option takes a list of all arguments required by the module
- One of the simplest ad hoc commands uses the ping module.
- It does not send an ICMP ping to the managed host.
- It checks to see if Ansible modules written in Python can be run on the managed hos
```bash
ansible all -m ping

rpi301 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "changed": false,
    "ping": "pong"
}
```
### Overriding Default Configuration Settings
- To override a default configuration setting there are several different options. 
- These options override the configuration in the **ansible.cfg** configuration file.
  - **-k** or **--ask-pass** will prompt for the connection password.
  - **-u REMOTE_USER** overrides the **remote_user** setting in **ansible.cfg**.
  - **-b** option enables privilege escalation, running operations with **become: yes**.
  - **-K** or **--ask-become-pass** will prompt for the privilege escalation password.
  - **--become-method** will override the default privilege escalation method. 
The default is **sudo**. Find valid choices using **ansible-doc -t become -l**
## Ansible playbooks
- An Ansible Playbook is the main way to automate tasks in Ansible.
- A playbook is a YAML-based text file containing a list of one or more plays to run in a specific order.
- A play is an ordered list of tasks run against specific hosts within an inventory.
- Each task runs a module that performs some simple action on or for the managed host.
- Most tasks are idempotent and can be safely run a second time without problems.
- Playbooks can change lengthy, complex manual administrative tasks into an easily repeatable routine
with predictable and successful outcomes.
### Playbook formatting
- A playbook is saved using the standard file extension .yml.
- Indentation with space character indicates the structure of the data in the file.
- Two‑space indentation with the space character only is the main concept behind the syntax within YAML files. Note that the spaces cannot be substituted with the tab character. The tab character is not allowed in proper YAML. YAML doesn't place strict requirements on how many spaces are used for the indentation.
- YAML does not place strict requirements on how many spaces are used for the indentation, but there
are two basic rules.
  - Data elements at the same level in the hierarchy (such as items in the same list) must have the
same indentation.
  - Items that are children of another item must be indented more than their parents.
- Only the space character can be used for indentation. Tab characters are not allowed.
```bash

```
## Ansible Getting Information about a Play
```bash
# List all tasks that would be executed by a play without making any changes to the remote servers
ansible-playbook myplaybook.yml --list-tasks
# List all hosts that would be affected by a play, without running any tasks on the remote servers
ansible-playbook myplaybook.yml --list-hosts
# List all tags available in a play
ansible-playbook myplaybook.yml --list-tags
```

## Ansible Controlling Playbook Execution
```bash
# Skip anything that comes before the specified task, executing the remaining of the play from that point on
ansible-playbook myplaybook.yml --start-at-task="Set Up Nginx"
# Only execute tasks associated with specific tags
ansible-playbook myplaybook.yml --tags=mysql,nginx
# Skip all tasks that are under specific tags
ansible-playbook myplaybook.yml --skip-tags=mysql
```

## Ansible Vault to Store Sensitive Data
```bash
# Creating a New Encrypted File
ansible-vault create credentials.yml
# Create a new encrypted file using a custom vault ID for dev env
ansible-vault create --vault-id dev@prompt credentials_dev.yml
# Create a new encrypted file using a custom vault ID for prod env
ansible-vault create --vault-id prod@prompt credentials_prod.yml
# Create a new encrypted file using a custom vault ID width password file
ansible-vault create --vault-id dev@path/to/passfile credentials_dev.yml
# Encrypt an existing Ansible file
ansible-vault encrypt credentials.yml
# View the contents of a file that was previously encrypted with ansible-vault
ansible-vault view credentials.yml
# Edit the contents of a file that was previously encrypted with Ansible Vault
ansible-vault edit credentials.yml
# Edit the contents of a file that was previously encrypted with Ansible Vault with custome vault ID
ansible-vault edit credentials_dev.yml --vault-id dev@prompt
# Decrypting Encrypted Files
ansible-vault decrypt credentials.yml
```

## Debugging
```bash
# Output verbosity
ansible-playbook myplaybook.yml -v
# Output more verbosity
ansible-playbook myplaybook.yml -vvvv
```

## Ansible Documentation
```bash
# List all ansible aws module documentations
ansible-doc -l | grep aws
```
