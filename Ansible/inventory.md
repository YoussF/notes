<!--
Source: https://app.pluralsight.com/library/courses/ansible-fundamentals/table-of-contents)
-->

<h1>Ansible - Managing the Inventory</h1>

<h3>Table of contents :</h3>

* [1. Creating a Static Inventory of Managed Hosts](#1-creating-a-static-inventory-of-managed-hosts)
  * [1.1 Introduction](#11-introduction)
  * [1.2 Specifying Managed Hosts with a Static Inventory](#12-specifying-managed-hosts-with-a-static-inventory)
  * [1.3 Inventory Location](#13-inventory-location)
  * [1.4 Creating an INI-Formatted Inventory File](#14-creating-an-ini-formatted-inventory-file)
  * [1.5 Special Groups and Group Names](#15-special-groups-and-group-names)
  * [1.6 Defining Nested Groups](#16-defining-nested-groups)
  * [1.7 Simplifying Host Specifications with Ranges](#17-simplifying-host-specifications-with-ranges)
  * [1.8 Alternative Inventory File Format: YAML](#18-alternative-inventory-file-format-yaml)
  * [1.9 Verifying the Inventory](#19-verifying-the-inventory)
* [2. Managing Connection Settings and Privilege Escalation](#2-managing-connection-settings-and-privilege-escalation)
  * [2.1 Ansible’s Agentless Architecture](#21-ansibles-agentless-architecture)
  * [2.2 Controlling Connections to Managed Hosts](#22-controlling-connections-to-managed-hosts)
  * [2.3 Configuring Ansible](#23-configuring-ansible)
  * [2.4 Configuration File Precedence](#24-configuration-file-precedence)
  * [2.5 Managing Settings in the Configuration File](#25-managing-settings-in-the-configuration-file)
  * [2.6 Connection Settings in the Configuration File](#26-connection-settings-in-the-configuration-file)
  * [2.7 Privilege Escalation Settings in the Configuration File](#27-privilege-escalation-settings-in-the-configuration-file)
  * [2.8 Managing Settings in the Configuration File](#28-managing-settings-in-the-configuration-file)
  * [2.9 Host-Based Connection Variables](#29-host-based-connection-variables)
  * [2.10 Host-Based Connection and Privilege Escalation Variables](#210-host-based-connection-and-privilege-escalation-variables)
  * [2.11 Example Host-Based Connection Variables File](#211-example-host-based-connection-variables-file)
  * [2.12 Preparation on the Managed Host](#212-preparation-on-the-managed-host)
<br/><br/>

## 1. Creating a Static Inventory of Managed Hosts
Objectives
* Implement and use Ansible inventory and host files.
* Explain the format of inventory files.
* Create an inventory file that defines a list of Linux-based managed hosts, defines groups, and assigns managed hosts to those groups.

### 1.1 Introduction
* An inventory defines a collection of hosts managed by Ansible.
* Hosts can be assigned to groups.
* Groups can be managed collectively.
* Groups can contain child groups.
* Hosts can be members of multiple groups.
* Variables can be set that apply to hosts and groups.
<br />

### 1.2 Specifying Managed Hosts with a Static Inventory
* One way to define an Ansible inventory is as a text file.
* It can be written in a number of formats -- most commonly in an INI-style or in YAML.
* This is called a static inventory, because the inventory needs to be manually updated.
* It is possible to create a dynamic inventory that is automatically generated and updated, but we will cover that later in this course.
<br />

### 1.3 Inventory Location
* The location of the inventory is controlled by your current Ansible configuration file
  * **ansible --version** will show you which configuration file is in use
* That file specifies the location of the inventory in its [defaults] section:
  ```ini
  [default]
  inventory = ./inventory
  ```
* If not set by the configuration, **/etc/ansible/hosts** is used
<br />

### 1.4 Creating an INI-Formatted Inventory File
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

### 1.5 Special Groups and Group Names
* Two host groups always exist:
  * **all** includes every host in the inventory
  * **ungrouped** includes every host in **all** that is not a member of another group
* Group names should not include dashes, but underscores are fine
* Avoid confusion: do not give a group the same name as a host!
<br />

### 1.6 Defining Nested Groups
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

### 1.7 Simplifying Host Specifications with Ranges
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

### 1.8 Alternative Inventory File Format: YAML
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

### 1.9 Verifying the Inventory
* You can use the ansible-inventory command to verify the inventory
* The -i option can be used to check any file rather than the current inventory
* The following command will display the current inventory in YAML format:
  ```bash
  ansible-inventory -y --list
  ```
* The ansible command can also verify a machine’s presence in the inventory.
 ```bash
 [user@contolnode ~]$ ansible washington1.example.com --list-hosts
   hosts (1):
     washington01.example.com
 [user@contolnode ~]$ ansible washington01.example.com --list-hosts
   [WARNING]: provided hosts list is empty: only localhost is available
   hosts (0):
 ```
*  If an inventory contains a host and a host group with the same name, the ansible command prints a warning and targets the host. The host group is ignored.

## 2. Managing Connection Settings and Privilege Escalation
Objectives
* Configure connections used for communicating with managed hosts.
* Use privilege escalation for playbook and play escalation.
* Explain how Ansible selects the configuration file to use and how it is applied.

### 2.1 Ansible’s Agentless Architecture
* Ansible does not require you to install a custom agent on managed hosts
* Protocols and software included with the operating system are leveraged
  * SSH and Python used on Linux systems
  * Other protocols used for things like Windows (Windows Remote Management and PowerShell)
* Advantages of using common, well-tested and understood tools
  * Simpler to prepare systems
  * Reduces security risks

### 2.2 Controlling Connections to Managed Hosts
Ansible on the control node needs some information to successfully connect to managed hosts:
* The location of the inventory file
* The connection protocol to use (by default, SSH)
* Whether a non-standard network port is needed to connect to the server
* What user it can login as
* If the user is not root, whether Ansible should escalate privileges to root
* How Ansible should become root (by default, with **sudo**)
* Whether to prompt for an SSH password to log in or a **sudo** password to gain privileges
You can set default selections for this information in your Ansible configuration file.

### 2.3 Configuring Ansible
The behaviour of an Ansible installation can be customized by modifying settings in the Ansible configuration file. Ansible chooses its configuration from one of several possible locations:
* The ANSIBLE_CONFIG environment variable (if set, its value is the path to the file)
* If it is not set, Ansible will look for the configuration file in the following places:
* **./ansible.cfg**
  * In the Ansible command's current working directory
* **~/.ansible.cfg**
  * As a "dot file" in the user's home directory, used if there is no **./ansible.cfg** file
* **/etc/ansible/ansible.cfg**
  * The default configuration file if no other configuration file is found

### 2.4 Configuration File Precedence
* **ansible --version** clearly identifies which configuration file is currently being used.
  ```bash
  user@conotrolnode:~$ ansible --version
  ansible 2.9.20
  config file = /etc/ansible/ansible.cfg
  configured module search path = ['/home/user/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/local/lib/python3.8/dist-packages/ansible
  executable location = /usr/local/bin/ansible
  python version = 3.8.5 (default, May 27 2021, 13:30:53) [GCC 9.3.0]
  ```
* You can use ansible-config --version to get the same information.

### 2.5 Managing Settings in the Configuration File
* ansible.cfg consists of several sections.
* Each section contains settings defined as key-value pairs.
* Section titles are enclosed in square brackets.
* Basic operations use two sections:
  * **[defaults]** sets defaults for Ansible operation.
  * **[privilege_escalation]** configures how Ansible performs privilege escalation on managed hosts.

### 2.6 Connection Settings in the Configuration File
* Settings to control your SSH connection can go in the **[defaults]** section:
  * **remote_user** specifies the user you want to use on the managed host (if you do not specify, it uses your current user name)
  * **remote_port** specifies what port sshd is using on the managed host
(if you do not specify, the default is 22)
  * **ask_pass** controls whether Ansible will prompt you for the SSH password
(it will not by default, assuming you are using SSH key-based authentication)

### 2.7 Privilege Escalation Settings in the Configuration File
* Settings to control privilege escalation can go in the **[privilege_escalation]** section:
  * **become** controls whether you will automatically use privilege escalation
(default is no, and you can override this at the command line or in playbooks)
  * **become_user** controls what user on the managed host Ansible should become
(default is root)
  * **become_method** controls how Ansible will become that user
(using sudo by default, there are other options like **su**)
  * **become_ask_pass** controls whether to prompt you for a password for your become method
(default is no)

### 2.8 Managing Settings in the Configuration File
* For example, the following is a typical **ansible.cfg** file:
  ```ini
  [defaults]
  inventory = ./inventory
  remote_user = ansible
  ask_pass = false
  [privilege_escalation]
  become = true
  become_user = root
  become_ask_pass = false
  ```

### 2.9 Host-Based Connection Variables
* You can also apply settings specific to a particular host by setting connection variables
* There are several ways to do this
* One of the easiest is to place the settings in a file in the host_vars directory in the same directory as your inventory file:
  ```
  project
  ├── ansible.cfg
  ├── host_vars
  │ ├── server1.example.com
  │ └── server2.example.com
  └── inventory
  ```
  * In the example at right, there are host-specific files for server1.example.com and server2.example.com
  * The hosts should appear with those names in the inventory
* These settings override the ones in ansible.cfg
* They also have slightly different syntax and naming

### 2.10 Host-Based Connection and Privilege Escalation Variables
* **ansible_host** specifies a different IP address or hostname to use for the connection for this host instead of the one in the inventory
* **ansible_port** specifies the port to use for the SSH connection on this host
* **ansible_user** specifies the user you want to use on this host
* **ansible_become** specifies whether to use privilege escalation for this host
* **ansible_become_user** specifies the user to become on this host
* **ansible_become_method** specifies the privilege escalation method to use for this host

### 2.11 Example Host-Based Connection Variables File
* For example, the contents of host_vars/server1.example.com could be:
  ```bssh
  ---
  # connection variables for server1.example.com
  ansible_host: 192.0.2.104
  ansible_port: 34102
  ansible_user: root
  ansible_become: false
  ```
* These settings only affect server1.example.com in the inventory

### 2.12 Preparation on the Managed Host
* One of the more common choices is to set up SSH key-based authentication to an unprivileged
account that can use **sudo** to become root without a password
* The advantage of this is that you can use a specific account that only Ansible uses, and tie that to a particular SSH private key, but still have "passwordless" authentication
* Alternatively: SSH key-based authentication to the unprivileged account, then require the **sudo** password for authentication to root
* Ansible allows you to select the mix of settings that works best for your security policy and stance



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