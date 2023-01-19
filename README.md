# Playbook for provisioning OpenVPN server

The target server for the provisioning can be set in **/etc/ansible/hosts** file or using the variable **openvpn_server**.
Used by OpenVPN server port can be set using variable **openvpn_server_port** (or will be used *default port - 1194*).
Authentification for the ansible provisioning by default is SSH key. 
The public SSH key should be copied  to the target server using the command **ssh-copy-id**:

    ssh-copy-id -i <~/.ssh/mykey.pub> <user@host>

Also, ansible can use password authentication if the target server supports it. 
In such a case, "**-k**" key should be added to the ansible-playbook run command.

**Playbook usage examples:**

    ansible-playbook vpn-playbook.yaml --extra-vars "openvpn_server=<my.openvpn.example.com> openvpn_server_port=12345" -k
    ansible-playbook vpn-playbook.yaml --extra-vars "openvpn_server=<my.openvpn.example.com>" -k

**Clone repo:**

    git clone --recursive https://github.com/smart-cn/openvpn-ansible.git

## Additional information about work with submodules (used submodule https://github.com/kyl191/ansible-role-openvpn):

Clone the repo with all submodules:

    git clone --recursive https://github.com/smart-cn/openvpn-ansible.git

Pull all changes in the repo including changes in the submodules:

    git pull --recurse-submodules

Pull only changes in the repo, excluding changes in the submodules:

    git pull

Update submodules to the latest commit in the configured *(default - main)* branch:

    git submodule update

Update submodules, **remote** key fetches new commits in the submodules and updates the working tree to the commit described by the branch:

    git submodule update --remote

Add submodule using main branch as the one you want to track

    git submodule add <URL to submodule repo> <folder for submodule>
    git submodule init 

Add submodule and define the **<branch-name>** branch as the one you want to track

    git submodule add -b <branch-name> <URL to submodule repo> <folder for submodule>
    git submodule init 
