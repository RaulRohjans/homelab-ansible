# Homelab Ansible
This Ansible project is designed to automate the setup and management of my homelab composed of a Debian server. <br />
The project includes roles to configure storage, automated backup solutions, Docker, and more, ensuring efficient and reliable operation of the homelab.


## Roles
- samba: Configures an SMB server for network file sharing.

- bagsplus_backup: Configures a cron job to back up the store databases multiple times a day.

- docker: Installs Docker and its dependencies.

- deploy_containers: Deploys containers within the Docker instance.

- setup_backups: Creates a daily backup script for Docker container storage and main file storage.


## Prerequisites

- Nodes must run Debian OS (other OS are untested!).

- Ensure SSH access is configured for Ansible to communicate with the nodes.

- Python and Ansible installed on the control machine.


## Installation

#### Clone the repository:

```
git clone https://github.com/raulrohjans/homelab-ansible.git

cd ansible-homelab
```
<br />

#### Update the Inventory:

Modify the hosts inventory file to include your node details.

```
[mainservers]
192.168.1.5 ansible_host=192.168.1.5

[all:vars]
ansible_user=raul
```
<br />

#### Update Variables:

Adjust any necessary variables in the "group_vars" folder to match your environment.


## Usage

#### Encrypt and Decrypt files:
All the files that contain sensitive information are encrypted with ansible-vault.
If you happen to know the password, you can use these commands to decrypt them

```
ansible-vault encrypt example.yml

ansible-vault decrypt example.yml
```

#### Run the Playbook:

```
ansible-playbook main.yml --ask-pass --ask-become-pass --ask-vault-pass
```


## Contributing

Contributions are welcome! Please submit a pull request with detailed information about your changes!


## License

This project is licensed under the MIT License. See the LICENSE file for more information.
