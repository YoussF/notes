<!--
Source: https://app.pluralsight.com/library/courses/ansible-fundamentals/table-of-contents)
-->

<h1>Ansible</h1>

Ansible is an open-source software provisioning, configuration management, and application-deployment tool enabling infrastructure as code. It runs on many Unix-like systems, and can configure both Unix-like systems as well as Microsoft Windows. It includes its own declarative language to describe system configuration. Ansible was written by Michael DeHaan and acquired by Red Hat in 2015. Ansible is agentless, temporarily connecting remotely via SSH or Windows Remote Management (allowing remote PowerShell execution) to do its tasks.

<h3>Table of contents :</h3>

<details>
  <summary>Click to view</summary>

* [Managing the inventory](#managing-the-inventory)
  * [Introduction](#introduction)
  * [Specifying Managed Hosts with a Static Inventory](#specifying-managed-hosts-with-a-static-inventory)
  * [Inventory Location](#inventory-location)
  * [Creating an INI-Formatted Inventory File](#creating-an-ini-formatted-inventory-file)
  * [Special Groups and Group Names](#special-groups-and-group-names)
  * [Defining Nested Groups](#defining-nested-groups)
  * [Simplifying Host Specifications with Ranges](#simplifying-host-specifications-with-ranges)
  * [Alternative Inventory File Format: YAML](#alternative-inventory-file-format-yaml)
  * [Verifying the Inventory](#verifying-the-inventory)
</details>
<br/><br/>

# Managing the inventory

## Introduction
* An inventory defines a collection of hosts managed by Ansible.
* Hosts can be assigned to groups.
* Groups can be managed collectively.
* Groups can contain child groups.
* Hosts can be members of multiple groups.
* Variables can be set that apply to hosts and groups.
<br />

## Specifying Managed Hosts with a Static Inventory
* One way to define an Ansible inventory is as a text file.
* It can be written in a number of formats -- most commonly in an INI-style or in YAML.
* This is called a static inventory, because the inventory needs to be manually updated.
* It is possible to create a dynamic inventory that is automatically generated and updated, but we will cover that later in this course.
<br />

## Inventory Location
* The location of the inventory is controlled by your current Ansible configuration file
  * **ansible --version** will show you which configuration file is in use
* That file specifies the location of the inventory in its [defaults] section:
  ```ini
  [default]
  inventory = ./inventory
  ```
* If not set by the configuration, **/etc/ansible/hosts** is used
<br />

## Creating an INI-Formatted Inventory File
* In its simplest form, an INI-formatted inventory file is a list of host names or IP addresses:
  ```ini
  web1.example.com
  web2.example.com
  db1.example.com
  db2.example.com
  192.0.2.42
  ```
* Host groups allow you to collectively automate a set of systems.
* In the following example, there are two groups, webservers and db_servers
  ```ini
  [webservers]
  web1.example.com
  web2.example.com
  192.168.2.42

  [db_servers]
  db1.example.com
  db2.example.com
  ```
* A host can be a member of multiple groups
* This allows you to organize groups in different ways depending on how you want to manage them:
  * Web servers or database servers
  * Servers in production or testing
  * Servers in the East data center or the West data center
    ```ini
    [webserver]
    web1.example.com
    web2.example.com
    102.168.2.42

    [db_servers]
    db1.example.com
    db2.example.com

    [east_datacenter]
    web1.example.com
    db1.example.com

    [west_datacenter]
    web2.example.com
    db2.example.com

    [production]
    web1.example.com
    web2.example.com
    db1.example.com
    db2.example.com

    [development]
    192.168.2.42
    ```
<br />

## Special Groups and Group Names
* Two host groups always exist:
  * **all** includes every host in the inventory
  * **ungrouped** includes every host in **all** that is not a member of another group
* Group names should not include dashes, but underscores are fine
* Avoid confusion: do not give a group the same name as a host!
<br />

## Defining Nested Groups
* Ansible host inventories can include groups of host groups.
* In an INI-formatted inventory, you can add nested host groups with the :children suffix.
* In this example, canada and usa are nested groups inside the group north_america
  ```ini
  [usa]
  washington01.example.com
  washington02.example.com

  [canada]
  antario01.example.com
  antario02.example.com

  [north_america:children]
  canada
  usa
  ```
<br />

## Simplifying Host Specifications with Ranges
* It is possible to specify ranges in the host names or IP addresses.
* Both numeric and alphabetic ranges can be specified.
* Ranges match all values from [START:END].
* Groups can contain child groups.
* For example:
  * **192.168.[4:7].[0:255]** matches all IPv4 addresses in the 192.168.4.0/22 network (**192.168.4.0
through 192.168.7.255**).
  * **server[01:20].example.com** matches all hosts named **server01.example.com through
server20.example.com**.
  * **[a:c].dns.example.com** matches hosts named **a.dns.example.com, b.dns.example.com, and
c.dns.example.com**.
* If leading zeros are included, they are used in the pattern.
  ```ini
  [usa]
  washington[1:2].example.com
  antario[01:02].example.com
  ```
* In this example, **ontario01.example.com** is a match but **ontario1.example.com** is not.
<br />

## Alternative Inventory File Format: YAML
* Inventory files can also be expressed in YAML format.
* A comparison of an INI-formatted inventory with an identical YAML-formatted inventory:
  * INI :
    ```ini
    [usa]
    washington1.example.com
    washington2.example.com
    [canada]
    ontario01.example.com
    ontario02.example.com
    [north_america:children]
    canada
    usa
    ```
  * YAML :
    ```yaml
    all:
      children:
        north_america:
          children:
            canada:
              hosts:
                ontario01.example.com: {}
                ontario02.example.com: {}
            usa:
              hosts:
                washington1.example.com: {}
                washington2.example.com: {}
    ```
<br />

## Verifying the Inventory
* You can use the ansible-inventory command to verify the inventory
* The -i option can be used to check any file rather than the current inventory
* The following command will display the current inventory in YAML format:
  ```bash
  ansible-inventory -y --list
  ```
* The ansible command can also verify a machine’s presence in the inventory.
  




















<!--

# Ansible running playbook
```bash
# Run a playbook and execute all the tasks defined within it
ansible-playbook myplaybook.yml
# Overwrite the default hosts option in the playbook and limit execution to a certain group or host
ansible-playbook -l server1 myplaybook.yml
```
# Ansible oneline modules
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
# Ansible config
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
## Host-Based Connection Variables
```bash
project
├── ansible.cfg
├── host_vars
│ ├── server1.example.com # These settings override the ones in ansible.cfg
│ └── server2.example.com # These settings override the ones in ansible.cfg
└── inventory
# They also have slightly different syntax and naming
```
## Host-Based Connection and Privilege Escalation Variables
- **ansible_host**: specifies a different IP address or hostname to use for the connection for this host 
instead of the one in the inventory
- **ansible_port**: specifies the port to use for the SSH connection on this host
- **ansible_user**: specifies the user you want to use on this host
- **ansible_become**: specifies whether to use privilege escalation for this host
- **ansible_become_user**: specifies the user to become on this host
- **ansible_become_method**: specifies the privilege escalation method to use for this host 
## Preparation on the Managed Host
- One of the more common choices is to set up SSH key-based authentication to an unprivileged 
account that can use sudo to become root without a password
- The advantage of this is that you can use a specific account that only Ansible uses, and tie that to a 
particular SSH private key, but still have "passwordless" authentication
- Alternatively: SSH key-based authentication to the unprivileged account, then require the sudo
password for authentication to root
- Ansible allows you to select the mix of settings that works best for your security policy and stance
# Ansible commands
- Ad hoc commands are simple, one line operations that are run without writing a playbook.
- They are useful for quick tests and changes.
- For example, to start a service or ensure a line exists in a file.
- Ad hoc commands have limitations.
# Ansible modules
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
# Ansible ad hoc commands
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
## Overriding Default Configuration Settings
- To override a default configuration setting there are several different options. 
- These options override the configuration in the **ansible.cfg** configuration file.
  - **-k** or **--ask-pass** will prompt for the connection password.
  - **-u REMOTE_USER** overrides the **remote_user** setting in **ansible.cfg**.
  - **-b** option enables privilege escalation, running operations with **become: yes**.
  - **-K** or **--ask-become-pass** will prompt for the privilege escalation password.
  - **--become-method** will override the default privilege escalation method. 
The default is **sudo**. Find valid choices using **ansible-doc -t become -l**
# Ansible playbooks
- An Ansible Playbook is the main way to automate tasks in Ansible.
- A playbook is a YAML-based text file containing a list of one or more plays to run in a specific order.
- A play is an ordered list of tasks run against specific hosts within an inventory.
- Each task runs a module that performs some simple action on or for the managed host.
- Most tasks are idempotent and can be safely run a second time without problems.
- Playbooks can change lengthy, complex manual administrative tasks into an easily repeatable routine
with predictable and successful outcomes.
## Playbook formatting
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
# Ansible getting information about a playbook
```bash
# List all tasks that would be executed by a play without making any changes to the remote servers
ansible-playbook myplaybook.yml --list-tasks
# List all hosts that would be affected by a play, without running any tasks on the remote servers
ansible-playbook myplaybook.yml --list-hosts
# List all tags available in a play
ansible-playbook myplaybook.yml --list-tags
```
# Ansible controlling playbook execution
```bash
# Skip anything that comes before the specified task, executing the remaining of the play from that point on
ansible-playbook myplaybook.yml --start-at-task="Set Up Nginx"
# Only execute tasks associated with specific tags
ansible-playbook myplaybook.yml --tags=mysql,nginx
# Skip all tasks that are under specific tags
ansible-playbook myplaybook.yml --skip-tags=mysql
```
# Ansible Vault to store sensitive datas
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
# Debugging
```bash
# Output verbosity
ansible-playbook myplaybook.yml -v
# Output more verbosity
ansible-playbook myplaybook.yml -vvvv
```
# Ansible documentation
```bash
# List all ansible aws module documentations
ansible-doc -l | grep aws
```

-->