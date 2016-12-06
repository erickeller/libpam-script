# pam-script for LUKS

## Introduction

This small project automatically install libpam-script and configure it accordingly.
When a user changes his password it will also update the following:

* luks encryption password
* gnome keyring password

## Important note

The following launchpad bug 
https://bugs.launchpad.net/ubuntu/+source/libpam-script/+bug/1411225

requires some workaround

```
cat << EOF > /usr/share/pam-configs/pam_script
Name: Support for authentication by external scripts
Default: yes
Priority: 257
EOF
pam-auth-update --package
```

## Try it out

you can try this out using vagrant

```
vagrant plugin install vagrant-lxc
vagrant up --provider lxc
vagrant ssh
# in the vagrant box
sudo useradd test
sudo passwd test
```

