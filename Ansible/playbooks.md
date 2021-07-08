<!--
Source: https://app.pluralsight.com/library/courses/ansible-fundamentals/table-of-contents)
-->

<h1>Ansible - Playbooks</h1>
  
<h3>Table of contents :</h3>

* [1. Introduction](#1-introduction)
  * [1.1 Writing Playbooks](#11-writing-playbooks)
* [2. Creating a Simple Playbook](#2-creating-a-simple-playbook)
  * [2.1 Formatting an Ansible Playbook](#21-formatting-an-ansible-playbook)
  * [2.2 Example: A simple playbook with one play, of one task](#22-example-a-simple-playbook-with-one-play-of-one-task)
  * [2.3 Running an Ansible Playbook](#23-running-an-ansible-playbook)
  * [2.4 Limiting Playbook Execution](#24-limiting-playbook-execution)
  * [2.5 Validating a Playbook](#25-validating-a-playbook)
* [3. Using Varaibles in Plays](#3-using-varaibles-in-plays)
  * [3.1 Introduction to Ansible Variables](#31-introduction-to-ansible-variables)
  * [3.2 Naming Variables](#32-naming-variables)
  * [3.3 Variable Scope](#33-variable-scope)
  * [3.4 Defining Variables](#34-defining-variables)
  * [3.5 Managing Variables in Playbooks](#35-managing-variables-in-playbooks)
  * [3.6 Referencing Variables in Playbooks](#36-referencing-variables-in-playbooks)
  * [3.7 Referencing Variables](#37-referencing-variables)
  * [3.8 Host Variables and Group Variables](#38-host-variables-and-group-variables)
  * [3.9 Using Directories to Set Host and Group Variables](#39-using-directories-to-set-host-and-group-variables)
  * [3.9 Using Directories to Set Host and Group Variables](#39-using-directories-to-set-host-and-group-variables-1)
  * [3.10 Defining Variables in Playbooks](#310-defining-variables-in-playbooks)
  * [3.11 Selecting Items from a Dictionary](#311-selecting-items-from-a-dictionary)
  * [3.12 The Register Statement](#312-the-register-statement)
* [4. Protecting Sensitive Data](#4-protecting-sensitive-data)
  * [4.1 Introduction to Ansible Vault](#41-introduction-to-ansible-vault)
  * [4.2 Create, View and Edit Encrypted Files](#42-create-view-and-edit-encrypted-files)


# 1. Introduction
This module demonstrates how to:

* Create a simple playbook.
* Create and reference variables in playbooks.
* Run conditional tasks.
* Trigger Tasks with Handlers
* Recover from Errors with Blocks
* Deploy Files with Jinja2 Templates
* Process Variables with Jinja2 Filters

## 1.1 Writing Playbooks
* An Ansible Playbook is the main way to automate tasks in Ansible.
* A playbook is a YAML-based text file containing a list of one or more plays to run in a specific order.
* A play is an ordered list of tasks run against specific hosts within an inventory.
* Each task runs a module that performs some simple action on or for the managed host.
* Most tasks are idempotent and can be safely run a second time without problems.
* Playbooks can change lengthy, complex manual administrative tasks into an easily repeatable routine
with predictable and successful outcomes.

# 2. Creating a Simple Playbook

## 2.1 Formatting an Ansible Playbook
* A playbook is saved using the standard file extension .yml.
* Indentation with space character indicates the structure of the data in the file.
* YAML does not place strict requirements on how many spaces are used for the indentation, but there
are two basic rules.
  * Data elements at the same level in the hierarchy (such as items in the same list) must have the
same indentation.
  * Items that are children of another item must be indented more than their parents.
* Only the space character can be used for indentation. Tab characters are not allowed.

## 2.2 Example: A simple playbook with one play, of one task
```YAML
---
- name: Converted ad hoc command example
  hosts: all
  become: yes
  tasks:
    - name: user exists with UID 4000
      user:
        name: newbie
        uid: 4000
        state: present
```
* A name for the play to help document
its intended purpose.
* Hosts or groups on which the play will
run, taken from the inventory.
* This play will perform privilege
escalation.
* The beginning of the list of tasks in the
play.
* Clear descriptive names for each task
help document what each task does.
* Each task uses one module to perform
the work, in this case **user**.
* Argument for the **user** module
to specify the user to manage, its UID
number, and that it should exist.

## 2.3 Running an Ansible Playbook
Use the **ansible-playbook** command to run a playbook:
```bash
[user@host ansible]$ ansible-playbook site.yml
PLAY [Converted ad hoc command example] *****************************************************
TASK [Gathering Facts] **********************************************************************
ok: [localhost]
TASK [user exists with UID 4000] ************************************************************
changed: [localhost]
PLAY RECAP **********************************************************************************
localhost : ok=2 changed=1 unreachable=0 failed=0 skipped=0 rescued=0 ignored=0
```

## 2.4 Limiting Playbook Execution
* You can also limit the hosts you target on a particular run with the **--limit** flag.
* The limit is a host pattern that further limits the hosts for the play.
* For example:
  * A play has **hosts: webservers** in its definition
  * You run the playbook containing the play with the **--limit datacenter2** option
  * datacenter2 and webservers are both groups in the inventory
  * The play will only run on hosts that are in both webservers and datacenter2
```bash
ansible-playbook site.yml --limit datacenter2
```

## 2.5 Validating a Playbook
* Syntax validation with **--syntax-check**.
  * Running **--syntax-check** on the playbook will verify that it can be ingested by ansible.
  * The option can either be before or after the playbook.
```
[student@workstation ~]$ ansible-playbook --syntax-check webserver.yml
ERROR! Syntax Error while loading YAML.
  mapping values are not allowed in this context

The error appears to have been in ...output omitted...: line 9, column 12, but may
be elsewhere in the file depending on the exact syntax problem.

The offending line appears to be:

- name: Apache started
    service:
           ^ here
```
You can use the **-C** option to perform a dry run of the playbook execution. This causes Ansible to report what changes would have occurred if the playbook were executed, but does not make any actual changes to managed hosts.
```
[student@workstation ~]$ ansible-playbook -C webserver.yml

PLAY [play to setup web server] ******************************************************

TASK [Gathering Facts] ***************************************************************
ok: [servera.lab.example.com]

TASK [latest httpd version installed] ************************************************
changed: [servera.lab.example.com]

PLAY RECAP ***************************************************************************
servera.lab.example.com     : ok=2    changed=1     unreachable=0     failed=0
```

# 3. Using Varaibles in Plays
Objectives

* Explain the key places where variables are commonly set.
* Explain the basic rules of variable precedence.
* Create and run a playbook that uses variables.

## 3.1 Introduction to Ansible Variables
* Ansible supports variables that you can use to store values for reuse throughout an Ansible project.
* This simplifies the creation and maintenance of a project and reduce the number of errors.
* Variables provide a convenient way to manage dynamic values.
* Examples of values that variables might contain:
  * Users to create, modify or delete.
  * Software to install or uninstall.
  * Services to stop, start, or restart.
  * Files to create, modify, or remove.
  * Archives to retrieve from the Internet, or to extract.

## 3.2 Naming Variables
* Variable names must start with a letter, and they can only contain letters, numbers, and underscores.
  
|Invalid variable names | Valid Variable names |
|--|--|
| web server <br/> web-server |  web_server |
| remote.file | remote_file|
| 1st file <br/> 1st_file | file_1 <br/> file1 |
| remoteserver$1 | remote_server_1 <br/> remote_server1|

## 3.3 Variable Scope
* **Global**
  * The value is set for all hosts.
  * Example: extra variables you set in the job template
* **Host**
  * The value is set for a particular host (or group).
  * Examples: variables set for a host in the inventory or a host_vars directory, gathered facts
* **Play**
  * The value is set for all hosts in the context of the current play.
  * Examples: **vars** directives in a play, **include_vars** tasks, and so on

## 3.4 Defining Variables
* If a variable is defined at more than one level, the level with the highest precedence wins.
* A narrow scope generally takes precedence over a wider scope.
* Variables that you define in an inventory are overridden by variables that you define in the playbook.
* Variables defined in a playbook are overridden by “extra variables” defined on the command line withthe -e option.
Details on exact variable precedence are available at
https://docs.ansible.com/ansible/latest/playbooks_variables.html#variable-precedence-where-sho
uld-i-put-a-variable

## 3.5 Managing Variables in Playbooks
* Variables can be defined in multiple ways.
* One common method is to place a variable in a vars block at the beginning of a play:
```yaml
- hosts: all
  vars:
    user_name: joe
    user_state: present
```
* It is also possible to define play variables in external files.
* Use vars_files at the start of the play to load variables from a list of files into the play:
```yaml
- hosts: all
  vars_files:
    - vars/users.yml
```

## 3.6 Referencing Variables in Playbooks
* After declaring variables, you can use them in tasks.
* Reference a variable (replace it with its value) by placing the variable name in double braces:**{{ variable_name }}**
* Ansible substitutes the variable with its value when it runs the task.
```yaml
- name: Example play
  hosts: all
  vars:
    user_name: joe
  
  tasks:
  # This line will read: Creates the user joe
    - name: Creates the user {{ user_name }}
      user:
        # This line will create the user named joe
        name: "{{ user_name }}"
        state: present
```

## 3.7 Referencing Variables
* When you reference one variable as another variable’s value, and the curly braces start the value, you must use quotes around the value.
* This prevents Ansible for interpreting the variable reference as starting a YAML dictionary.
* The following message appears if the quotes are missing:
```
The offending line appears to be:
- systemd:
    name: {{ service }}
          ^ here

We could be wrong, but this one looks like it might be an issue with
missing quotes. Always quote template expression brackets when they
start a value. For instance:

with_items:
  - {{ foo }}

Should be written as:

 with_items:
   - "{{ foo }}"
```

## 3.8 Host Variables and Group Variables
* Host variables apply to a specific host.
* Group variables apply to all hosts in a host group or in a group of host groups.
* Host variables take precedence over group variables, but variables defined inside a play take
precedence over both.
* Host variables and group variables can be defined
  * In the inventory itself.
  * In **host_vars** and **group_vars** directories in the same directory as the inventory.
  * In **host_vars** and **group_vars** directories in the same directory as the playbook.
These are host and group based but have higher precedence than the inventory variables.

## 3.9 Using Directories to Set Host and Group Variables
* In the same directory as your playbook, create two directories, **group_vars** and **host_vars**.
  * To define group variables for the **servers** group, you would create a file named
**group_vars/servers**.
  * In that file, set variables to values, using YAML syntax. (The example at right sets ansible_user to a string and newfiles to a list of values.)
* To define host variables for a particular host, create a file with a name matching the host in the **host_vars** directory.
```
ansible_user: devops
newfiles:
  - /tmp/a.conf
  - /tmp/b.conf
```

## 3.9 Using Directories to Set Host and Group Variables
* Set host and group variables in **host_vars** and **group_vars** directories in the same directory as your playbook
* Works just like the host or group variables in your inventory
* They have host scope just like inventory variables
* These “playbook” host and group variables have slightly higher precedence than inventory variables (and override them)
* The files or directories in **host_vars** and **group_vars** have the name of the host or group they apply to
* If you use a directory for the host or group name, it can contain multiple variable files which are all used
```
project
├── group_vars
│   ├── all
│   ├── datacenters
│   ├── datacenters1
│   └── datacenters2
├── host_vars
│   ├── demo1.example.com
│   ├── demo2.example.com
│   ├── demo3.example.com
│   └── demo4.example.com
└── playbook.yml
```

## 3.10 Defining Variables in Playbooks
* Below is an example of a play level variable defined in a playbook.
* The dictionary that stores the variable values is listed at the first indentation.
* This makes it easier to update the list of packages, especially if the list is used in several tasks
```yaml
- name: Install packages
  hosts: all
  # Dictionary named vars at the play level.
  vars:
    # Name of variable.
    packages:
      # List of values.
      - nmap
      - httpd
      - php
      - mod_php
      - mod_ssl
  tasks:
    - name: Install software
      yum:
        # The packages variable expands to a list of packages for the yum module to install.
        name: "{{ packages }}"
        state: present
```

## 3.11 Selecting Items from a Dictionary
Arrays are multiple variables that can be browsed. It is possible to return one value from the array of values within a variable.
```yaml
vars:
  users:
    aditya:
      uname: aditya
      fname: Aditya
      lname: Atwal
      home: /home/aditya
      shell: /bin/bash
    carlotta:
      uname: carlotta
      fname: Carlotta
      lname: Spencer
      home: /home/carlotta
      shell: /bin/zsh
```
* To return the value of Aditya in this example, we would use the following syntax: **users[‘aditya’][‘fname’]**
* To grab Carlotta’s home directory reference **users[‘carlotta’][‘home’]**

## 3.12 The Register Statement
The **register** statement will capture the output of a command or task. The output is saved into a temporary variable that can be used later in the playbook for either debugging purposes or to achieve something else, such as a particular configuration based on a command's output.
* Return values vary for each module.
* Registered variables are only stored in memory.

# 4. Protecting Sensitive Data
Objectives
* Encrypt files containing sensitive data using Ansible Vault
* Run playbooks that reference Ansible Vault-encrypted files
* Update Ansible Vault-encrypted files

## 4.1 Introduction to Ansible Vault
* Ansible Playbooks sometimes need access to sensitive data.
  * Passwords, API keys, other secrets
* These secrets are often passed to Ansible through variables.
* It is a security risk to store these secrets in plain text files.
* Ansible Vault provides a way to encrypt and decrypt files used by playbooks
* The **ansible-vault** command is used to manage these files

## 4.2 Create, View and Edit Encrypted Files
* You will need to provide a password to use or manipulate an Ansible Vault encrypted file
* Create a new encrypted file using the command
  ```
  ansible-vault create filename
  ```
* View an encrypted file using the command
  ```
  ansible-vault view filename
  ```
* Edit an an encrypted file using the command
  ```
  ansible-vault edit filename
  ```