# Droplets provisionning

Custom Ansible playbooks in order to provision easily a lot of droplets for students (or for you).

Using the following collection: https://docs.ansible.com/ansible/2.10/collections/community/digitalocean/

## Prerequisites

Install Ansible, Python-Pip and dopy module.

``` $ cat install-ansible.sh
sudo yum install epel-release
sudo yum install ansible
sudo yum install python-pip
sudo pip install 'dopy>=0.3.5,<=0.3.5'

```

## Usage

- Create with single admin ssk key, configure each droplet with a user/password SSH connection. 
If you don't want so much security, it can create a basic user and a password for easy connection.

```
do_token: ''
do_admin_pub_key_name: ''
do_admin_pub_key: ''
droplets:
  - for: "The user"
    name: "thuser"
droplets_username: user
droplets_password: user
```

- Create each droplet with custom ssh key. 
If you wan't to login on droplets with ssh keys, you need to configure for each droplet the public key
that will be authorized. You need to specify for each droplet the `ssh_pub_key` to use.

```
do_token: ''
droplets:
  - for: "The user"
    name: "thuser"
    ssh_pub_key: 'ssh-rsa 1234 yourworkstation'
```