# Ansible-SetupComputer
An ansible playbook to setup a desktop machine utilizing gnome. 

Better explanation of the playbook are written on the roles.

## Running the playbook
The playbook is run as follows: 
```shell
ansible-playbook playbook.yml -K --ask-vault-pass
```

If there are no encrypted variables in your playbook ```--ask-vault-pass``` can be left out. 

Most of the commands are run as root. 

## License 

BSD