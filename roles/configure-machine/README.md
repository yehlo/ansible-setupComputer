configure-machine
=========

This role does...:
* ...Edit mounts as configured
* ...install and configure zsh
* ...edit dconf settings
* ...installs and enables gnome extensions

The Task to install gnome extensions was copied and modified from: 
https://github.com/jaredhocutt/ansible-gnome-extensions  

Requirements
------------

none

Role Variables
--------------

### mountpoints
All mountpoints can be configured in a dict. 

```yaml
mountpoints: 
  mount_nfsShare: 
    dst: location on local machine
    src: server:/path
    fstype: nfs4
    options: "my options"
  mount_cifsShare: 
    dst: location on local machine
    src: "//server/path" -> " is needed 
    fstype: nfs4
    options: "my options"
```

In case the options include user credentials it is adviced to encrypt those using ```ansible-vault```. 

```
ansible-vault encrypt_string "my options"
``` 

copy the output into the file as so: 
```yaml
options: !vault |
          encrypted data
```

### zsh_configuration
Currently this part can be ignored it is for future purposes. 

### gnome_configuration
To edit your local gnome desktop environment yoo can use the given dictionary. 

```yaml
gnome_configuration: 
  gtk_theme: 
    key: '/org/gnome/desktop/interface/gtk-theme'
    value: "'Numix'"
  icon_theme: 
    key: '/org/gnome/desktop/interface/icon-theme'
    value: "'Numix-Circle-Light'"
  ...
```

An unlimited amount of dconf settings can be added. 
To get a sense on how you can work with dconf you can either use the console program ```gsettings``` or the desktop application ```dconf-editor``` The keys and values are always listed. 

#### A short note on the value
If the value is a string it has to be entered like ```"'string'"``` 
If the value is a boolean it has to be entered like ```'true'```

### gnome_extension_ids
All extension ids can be added in form of an array to this variable. 

```yaml
gnome_extension_ids:
  - 15 # This is the id of alternate tab
  - 779 # This is the id of clipboard indicator
  - 945 # This is the id of cpu manager
```

You can find the needed ids on https://extensions.gnome.org/ They are inside of the url of the extension itself. 

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