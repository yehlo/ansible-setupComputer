Initialize-machine
=========

This role prepares the local machine to be configured. 
The role does...: 
* ...add repositories
* ...update the currently installed software
* ...install dnf packages and pip modules
* ...enable services to reduce power consumption

Requirements
------------

* dnf module version >= 2.0.1
* python-dnf 
* python version >= 2.6
* git >= 1.7.1

To make use of the pip module, pip has to be installed beforehand. 

Role Variables
--------------

The following 5 variables can be defined as follows: 

### dnf_packages
An array of packages. 

```yaml
dnf_packages:
  - vim
  - pip
  - git
  - ... 
```

### rpm_repositories
An array of all repositories to be added. 
The links need to end in .rpm or .repo

If the link ends in .repo ansible makes use of get_url and downloads the file directly into /etc/yum.repos.d/file.repo

```yaml
rpm_repositories:
  - https://fullpath.rpm
  - ... 
```
### pip_modules_root
An array of pip modules that need to be installed as the root user. 
(On most instances the modules should be installed as the executing user)

```yaml
pip_modules_root:
  - psutil
  - ... 
```

### pip_modules
An array of pip modules that are to be installed as the current user.

```yaml
pip_modules_root:
  - ... 
```

### rpm_keys
An array of all rpm keys that need to be added.
Currently one one key for microsoft visual studio code was needed, 

```yaml
pip_modules_root:
  - https://pathToKey.asc
```

Dependencies
------------

none

Example Playbook
----------------

This playbook is meant to be executed on the local machine. 

    - hosts: localhost
      roles:
         - initialize-Machine

License
-------

BSD