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


## 1. Introduction
This module demonstrates how to:

* Create a simple playbook.
* Create and reference variables in playbooks.
* Run conditional tasks.
* Trigger Tasks with Handlers
* Recover from Errors with Blocks
* Deploy Files with Jinja2 Templates
* Process Variables with Jinja2 Filters

### 1.1 Writing Playbooks
* An Ansible Playbook is the main way to automate tasks in Ansible.
* A playbook is a YAML-based text file containing a list of one or more plays to run in a specific order.
* A play is an ordered list of tasks run against specific hosts within an inventory.
* Each task runs a module that performs some simple action on or for the managed host.
* Most tasks are idempotent and can be safely run a second time without problems.
* Playbooks can change lengthy, complex manual administrative tasks into an easily repeatable routine
with predictable and successful outcomes.

## 2. Creating a Simple Playbook

### 2.1 Formatting an Ansible Playbook
* A playbook is saved using the standard file extension .yml.
* Indentation with space character indicates the structure of the data in the file.
* YAML does not place strict requirements on how many spaces are used for the indentation, but there
are two basic rules.
  * Data elements at the same level in the hierarchy (such as items in the same list) must have the
same indentation.
  * Items that are children of another item must be indented more than their parents.
* Only the space character can be used for indentation. Tab characters are not allowed.

### 2.2 Example: A simple playbook with one play, of one task
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

### 2.3 Running an Ansible Playbook
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

### 2.4 Limiting Playbook Execution
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

### 2.5 Validating a Playbook
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