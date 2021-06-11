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
