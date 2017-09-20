#  pi

## Table of Contents

  * [Requirements](#requirements)
  * [Pi Setup](#pi-setup)
  * [Ansible](#ansible)
  * [Vagrant lab](#vagrant-lab)

## Requirements

* [rasbian](https://www.raspberrypi.org/downloads/raspbian/)
* [ansible](http://docs.ansible.com/ansible/latest/intro_installation.html)
* [realvnc-vnc-viewer](https://www.realvnc.com/en/connect/download/viewer/)


## Pi Setup

Installing raspbian
```
# download 2017-09-07-raspbian-stretch.zip and unzip
# wget https://downloads.raspberrypi.org/raspbian_latest
# unzip raspbian_latest
unzip 2017-09-07-raspbian-stretch.zip

# insert card
# unmount if your system auto-mounts
sudo umount /dev/mmcblk0
sudo umount /dev/mmcblk1

# format to FAT 32
# I had to install dosfstools
sudo mkdosfs -F 32 -v /dev/mmcblk0

# dd
sudo dd bs=1M if=2017-09-07-raspbian-stretch.img of=/dev/mmcblk0
```

First time login with:
* user: pi
* pass: raspberry

* Enable ssh
* Enable vnc server
* reboot

Configure passwordless ssh
```
ssh-keygen -b 4096 -t rsa -f ~/.ssh/pi_rsa
ssh-copy-id -i ~/.ssh/pi_rsa pi@192.168.1.114
ssh-add ~/.ssh/pi_rsa
```

Install [realvnc-vnc-viewer](https://www.realvnc.com/en/connect/download/viewer/) locally to remote into pi desktop

Run vncviewer to connect with default creds: pi, raspberry

## Ansible

Update IP for your raspberry pi
```
[pi]
pi ansible_host=192.168.1.114 ansible_user=pi
```

* run ansible playbook on the pi
```
ansible-playbook -l pi site.yml 
```

## Vagrant lab

```
vagrant up
ansible-playbook -l vagrant site.yml 
```
