<!--
Source: https://app.pluralsight.com/library/courses/ansible-fundamentals/table-of-contents)
-->

<h1>Ansible - Commands</h1>

<h3>Table of contents :</h3>

* [1. Running Ad-Hoc Commands](#1-running-ad-hoc-commands)
  * [1.1 Ad Hoc Commands](#11-ad-hoc-commands)
  * [1.2 Ansible Modules](#12-ansible-modules)
  * [1.3 Running Ad Hoc Commands](#13-running-ad-hoc-commands)
  * [1.4 Overriding Default Configuration Settings](#14-overriding-default-configuration-settings)
  * [1.5 Ansible Modules](#15-ansible-modules)
  * [1.6 Selected Ansible Command-line Options](#16-selected-ansible-command-line-options)
* [2. Selecting Modules for Ad Hoc Commands](#2-selecting-modules-for-ad-hoc-commands)
  * [2.1 Finding Information about Ansible Modules](#21-finding-information-about-ansible-modules)
  * [2.2 Selected Ansible Modules](#22-selected-ansible-modules)
  * [2.3 Getting Information about an Ansible Module](#23-getting-information-about-an-ansible-module)
  * [2.4 Ad Hoc Command Example: User Creation](#24-ad-hoc-command-example-user-creation)
  * [2.5 Ad Hoc Command Example: Group Management](#25-ad-hoc-command-example-group-management)
  * [2.6 Ad Hoc Command Example: Software Package Installation](#26-ad-hoc-command-example-software-package-installation)
  * [2.7 Command Modules](#27-command-modules)
  * [2.8 Running Arbitrary Commands on Managed Hosts](#28-running-arbitrary-commands-on-managed-hosts)
  * [2.9 When to Use Ad Hoc Commands](#29-when-to-use-ad-hoc-commands)

## 1. Running Ad-Hoc Commands
Objectives
This module explains how Ansible automation tasks can use ad hoc commands to execute a single Ansible
task quickly.

### 1.1 Ad Hoc Commands
* Ad hoc commands are simple, one line operations that are run without writing a playbook.
* They are useful for quick tests and changes.
* For example, to start a service or ensure a line exists in a file.
* Ad hoc commands have limitations.

### 1.2 Ansible Modules
* Ansible provides modules, code that can be used to automate particular tasks
* Some uses of modules:
  * Ensure users exist with certain settings
  * Make sure the latest version of a software package is installed
  * Deploy a configuration file to a server
  * Enable a network service and make sure that it is running
* Most modules are idempotent, which means they only make changes if a change is needed.
Idempotent modules can be run safely multiple times.
* An ad hoc command runs one module on the specified managed hosts.

### 1.3 Running Ad Hoc Commands
* The **ansible** command runs an ad hoc command
* Its **host-pattern** argument specifies the managed hosts to run on.
* Its **-m** option names the module that Ansible should run.
* Its **-a** option takes a list of all arguments required by the module.
  ```bash
  ansible host-pattern -m module [-a 'module arguments'] [-i inventory]
  ```
* One of the simplest ad hoc commands uses the **ping** module.
* It does not send an ICMP ping to the managed host.
* It checks to see if Ansible modules written in Python can be run on the managed host.
  ```bash
  user@controlnode:~$ ansible all -m ping
  example.com | SUCCESS => {
      "ansible_facts": {
          "discovered_interpreter_python": "/usr/bin/python"
      },
      "changed": false,
      "ping": "pong"
  }
  ```

### 1.4 Overriding Default Configuration Settings
* To override a default configuration setting there are several different options.
* These options override the configuration in the ansible.cfg configuration file.
  * **-k** or **--ask-pass** will prompt for the connection password.
  * **-u REMOTE_USER** overrides the **remote_user** setting in **ansible.cfg**.
  * **-b** option enables privilege escalation, running operations with **become: yes**.
  * **-K** or **--ask-become-pass** will prompt for the privilege escalation password.
  * **--become-method** will override the default privilege escalation method.
The default is **sudo**. Find valid choices using **ansible-doc -t become -l**.

### 1.5 Ansible Modules
* Most modules take arguments to control them.
* Use the -a option to pass arguments.
* This example uses the user
module to make sure the user
newbie is present and has the
UID number 4000.
```bash
user@controlnode:~$ ansible -m user -a "name=newbie uid=4000 state=present" example.com
example.com | CHANGED => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "changed": true,
    "comment": "",
    "create_home": true,
    "group": 4000,
    "home": "/home/newbie",
    "name": "newbie",
    "shell": "/bin/sh",
    "state": "present",
    "system": false,
    "uid": 4000
}
```

### 1.6 Selected Ansible Command-line Options
A number of command line directives can be used to override options from the Ansible configuration file:
|Configuration File Directives|Command-line Option|
|---|---|
|inventory|--inventory, --inventory-file, -i|
|remote_user|--user, -u|
|become|--become, -b|
|become-method|--become-method|
|become_user|--become-user|
|become_ask_pass|--ask-become-pass, -K|

## 2. Selecting Modules for Ad Hoc Commands
Objective
* This module explains how Ansible ad hoc commands leverage Ansible modules to perform singular
command line interactions with managed hosts.

### 2.1 Finding Information about Ansible Modules
* The **ansible-doc -l** command lists all modules installed on a system.
* The name and a description of the module are displayed.
* Thousands of modules are available: consider piping the output into **grep** to filter the result.
* The same information is available from the Ansible website:
https://docs.ansible.com/ansible/latest/modules/modules_by_category.html

### 2.2 Selected Ansible Modules
There are thousands of modules to perform tasks. Some selected modules include:
* File Modules:
  * **copy**: Copy a local file to the manages host
  * **file**: Set permissions and other properties of files
  * **lineinfile**: Ensure a particular line is or is not in a file
  * **synchronize**: Synchronize content using rsync
* Software package modules:
  * **yum**: Manage packages using YUM
  * **dnf**: Manage packages using DNF
  * **gem**: Manage Ruby gems
* System Modules:
  * **firewalld**: Manage arbitrary ports and services using firewalld
  * **reboot**: Reboot a machine
  * **service**: Manage services
  * **user**: Add, remove, and manage user accounts
* Net Tools modules:
  * **get_url**: Download files over HTTP, HTTPS, or FTP
  * **nmcli**: Manage networking
  * **uri**: Interact with web services and communicate with APIs

### 2.3 Getting Information about an Ansible Module
* **ansible-doc** can also provide information on how to use a module.
* For example:
  ```bash
  user@controlnode:~$ ansible-doc ping
  > PING    (/usr/local/lib/python3.8/dist-packages/ansible/modules/system/ping.py)

          A trivial test module, this module always returns `pong' on successful contact. It does not make sense in playbooks, but it is useful from `/usr/bin/ansible'
          to verify the ability to login and that a usable Python is configured. This is NOT ICMP ping, this is just a trivial test module that requires Python on the
          remote-node. For Windows targets, use the [win_ping] module instead. For Network targets, use the [net_ping] module instead.

    * This module is maintained by The Ansible Core Team
  OPTIONS (= is mandatory):

  - data
          Data to return for the `ping' return value.
          If this parameter is set to `crash', the module will cause an exception.
          [Default: pong]
          type: str

  [..output omitted..]
  ```

### 2.4 Ad Hoc Command Example: User Creation
* You can use the ansible-doc -l command to discover the user module
  ```bash
  user              Manage user accounts
  ```
* Then run **ansible-doc** user to find out how the module works:
  * **name** (or user) is a mandatory argument, takes the user name of the account.
  * **uid** specifies the UID number that the account must have.
  * **state** specifies whether the user must be present or must be absent from the managed host.
This can be used to remove user accounts.
  * There are many other options to adjust the user's account settings and password.
* To make sure user newbie with UID 4000 exists on all managed hosts, you can run:
user Manage user accounts
ansible all -m user -a 'name=newbie uid=4000 state=present
```bash
ansible all -m user -a 'name=newbie uid=4000 state=present'
```

### 2.5 Ad Hoc Command Example: Group Management
* The **user** module can be used to adjust group membership.
* Run **ansible-doc** user again to find out how the module works:
  * **group** sets the user's primary group
  * **groups** is a list of other groups to assign the user
  * **append** controls whether to add the groups to the user's current list (if any) or replace the list
* To add user newbie to group developers and group wheel, without changing the user's primary group
or removing newbie from other groups:
```bash
ansible all -m user -a 'name=newbie groups=developers,wheel append=yes state=present'
```

### 2.6 Ad Hoc Command Example: Software Package Installation
* You can use the ansible-doc -l command to discover the package module
  ```bash
  package              Generic OS package manager
  ```
* Then run **ansible-doc** package to find out how the module works:
  * **name** is the name of a package or a list of packages to manage
  * **state** specifies whether the package must be present, absent, or the latest version.
This can be used to remove or update packages.
* To make sure the httpd package is installed on all hosts, you can run:
```bash
ansible all -m package -a 'name=httpd state=present'
```
* Other modules are also available, including **yum, dnf, and apt**, that work in a similar way but which
might support more sophisticated options specific to those managers.

### 2.7 Command Modules
* There are a handful of modules that run commands directly on the managed host
* You can use these if no other module is available to do what you need
* They are **not idempotent**: you must make sure that they are safe to run twice when using them
* **command** runs a single command on the remote system
* **shell** runs a command on the remote system's shell (redirection and other features work)
* **raw** simply runs a command with no processing (can be dangerous)
* In general, you should use regular modules if you can before resorting to these

### 2.8 Running Arbitrary Commands on Managed Hosts
* The **command** module allows administrators to run arbitrary commands.
* It cannot access shell environment variables or perform shell operations such as redirection and
piping.
  ```bash
  [user@controlnode ~]$ ansible mymanage@hosts -m command -a /usr/bin/hostname
  host1.lab.example.com | CHANGED | rc=0 >>
  host1.lab.example.com
  host2.lab.example.com | CHANGED | rc=0 >>
  host2.lab.example.com
  ```
* The **shell** module is used when commands require shell processing.
  ```bash
  [user@controlnode ~]$ ansible localhost -m command -a set
  localhost | FAILED | rc=2 >>
  [Errno 2] No such file or directory
  [user@controlnode ~]$ ansible localhost -m shell -a set
  localhost | CHANGED | rc=0 >>
  BASH=/bin/sh
  ```
* Both the **command** and **shell** modules require a working Python installation on the managed host.
* The **raw** module can run commands directly using the remote shell, bypassing the module subsystem.
* This is useful when managing systems that cannot have Python installed (for example a network
router).
### 2.9 When to Use Ad Hoc Commands
* Ad hoc commands are useful when you need to make one quick change to a large number of systems
* This can be very powerful when you need to make a simple change quickly
* However, they have a number of disadvantages:
  * You can only call one module, which limits them to simple changes
  * You have to type the same command again to rerun it, options can get complex
  * They are still semi-manual in nature
* In many cases, a better approach will be to use Ansible Playbooks
  * Playbooks can run multiple modules with conditionals and other processing
  * Playbooks are text files that can be tracked in version control systems
  * Playbooks can be easily rerun with a simple command
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