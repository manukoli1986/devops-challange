# devops-challange


Provisioned Flask Webapp using Vagrant and Ansible
==================================================

This repository contains the basics for developing a Flask application
within a Vagrant VM, using Ansible for provisioning.

Instructions to follow:
To start provisioning, we need to have vagrant installed on local computer or cloud. Basically automated task is only tested on Local setup.

1. clone this below repo:

```
#git clone https://github.com/manukoli1986/devops-challange.git
```

2. Boot up your Vagrant environment:
```
#vagrant up
```
If you get any error during bootup use any below command 

```
#vagrant up --provision
OR
#vagrant reload --provision
```


_This may take less or more than a minute depending on your internet connection (so be patient)._ 

Once Vagrant is UP and running, you will be seeing below message:

```
#vagrant up --provision
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Importing base box 'ubuntu/trusty64'...
==> default: Matching MAC address for NAT networking...
==> default: Setting the name of the VM: project_default_1557679451687_4759
==> default: Clearing any previously set forwarded ports...
==> default: Clearing any previously set network interfaces...
==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
    default: Adapter 2: bridged
==> default: Forwarding ports...
    default: 5000 (guest) => 5000 (host) (adapter 1)
    default: 22 (guest) => 2222 (host) (adapter 1)
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 127.0.0.1:2222
    default: SSH username: vagrant
    default: SSH auth method: private key
    default: Warning: Connection reset. Retrying...
    default: Warning: Connection aborted. Retrying...
    default:
    default: Vagrant insecure key detected. Vagrant will automatically replace
    default: this with a newly generated keypair for better security.
    default:
    default: Inserting generated public key within guest...
    default: Removing insecure key from the guest if it's present...
    default: Key inserted! Disconnecting and reconnecting using new SSH key...
==> default: Machine booted and ready!
==> default: Checking for guest additions in VM...
    default: The guest additions on this VM do not match the installed version of
    default: VirtualBox! In most cases this is fine, but in rare cases it can
    default: prevent things such as shared folders from working properly. If you see
    default: shared folder errors, please make sure the guest additions within the
    default: virtual machine match the version of VirtualBox you have installed on
    default: your host and reload your VM.
    default:
    default: Guest Additions Version: 4.3.40
    default: VirtualBox Version: 6.0
==> default: Setting hostname...
==> default: Configuring and enabling network interfaces...
==> default: Mounting shared folders...
    default: /vagrant => C:/Users/JYOTI/Downloads/project
==> default: Running provisioner: ansible_local...
    default: Installing Ansible...
Vagrant has automatically selected the compatibility mode '2.0'
according to the Ansible version installed (2.7.10).

Alternatively, the compatibility mode can be specified in your Vagrantfile:
https://www.vagrantup.com/docs/provisioning/ansible_common.html#compatibility_mode
    default: Running ansible-playbook...

PLAY [Configure Application] ***************************************************

TASK [Gathering Facts] *********************************************************
ok: [default]

TASK [Install Git] *************************************************************
changed: [default]

TASK [Install python3-pip] *****************************************************
changed: [default]

TASK [git] *********************************************************************
changed: [default]

TASK [Installing modules from requirment file.] ********************************
changed: [default]

TASK [Installing gunicorn module] **********************************************
changed: [default]

TASK [Run webapp script!] ******************************************************
changed: [default]

PLAY RECAP *********************************************************************
default                    : ok=7    changed=6    unreachable=0    failed=0

```

3. Our webapp is deployed now lets get connect to it using below IP address. For your case you need to run another command to get your vagrant guest machine's IP. 

```
#curl -s 192.168.0.107:5000

{"headers":{"Accept":"*/*","Host":"192.168.0.107:5000","User-Agent":"curl/7.64.0"},"origin":"192.168.0.101"}



#vagrant ssh -c "hostname -I | cut -d' ' -f2" 2>/dev/null
192.168.0.107
```



4. Vagrant runs the virtual machine without a UI. To prove that it is running, you can SSH into the machine:
```
#vagrant ssh
```


(*)Took help from vagrant-ansible docs
