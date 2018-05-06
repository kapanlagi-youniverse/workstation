# Moving from OSX to Ubuntu for realzies

## Pre-Tasks

    sh -c "$(wget -qO - https://raw.githubusercontent.com/KMK-Online/workstation/master/install.sh)"

### Enable sudo password less:

    sudo visudo

    # modify this line:
    %sudo ALL=(ALL:ALL) ALL
    # change to:
    %sudo ALL=(ALL:ALL) NOPASSWD:ALL

    # Enable ssh key login
    sudo vi /etc/ssh/sshd_config

    # uncomment this line:
    AuthorizedKeysFile %h/.ssh/authorized_keys

### You're ready to provisioning with

    ./all.sh workstation.yml

Which expands to:

    ansible-galaxy install -r ~/Workspace/workstation/requirements.yml
    ansible-playbook -i 127.0.0.1, ~/Workspace/workstation/workstation.yml -vvvv

If you are provisioning a laptop you will want to add:

    ./all.sh tommy.yml --extra-vars "laptop=true"

#### Misc ToDo:
[ ] Workstation machine locking automatically
[ ] Check Garuda's setup Ubuntu setup script, should use workstation
