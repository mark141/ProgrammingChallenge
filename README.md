# ProgrammingChallenge

Step-by-step introduction on using the docker deployment of the [get-started app from docker](https://docs.docker.com/get-started/02_our_app/)

## Install ansible on your Ubuntu environment - you might need to install pip first

  `python3 -m pip install ansible`
  
  Add this line to your .bashrc or .zshrc file:
  
  `export PATH=$PATH:$HOME/.local/bin`
  
## Install the Docker Galaxy Extension for Ansible

  `ansible-galaxy collection install community.docker`
  
## Configure the Ansible Environment

Change the `remote_user` and the `private_key_file` in the ansible.cfg 

```
[defaults]

inventory = inventory

host_key_checking = False  # optional: removes the SSH prompt 

deprecation_warnings = False  # optional: removes deprecation warning in playbooks

remote_user = <remote-user>
private_key_file = <remote-user-private-key-file>
```

## Set the desired Port in the Playbook

You can set the desired Port in the `deploy_docker.yaml` Playbook by changing the variable for `port_number`.

## Install the App with the `deploy_docker.yaml` Playbook

Use this command:

`python3 /home/<user>/.local/bin/ansible-playbook deploy_docker.yaml -e 'ansible_python_interpreter=/usr/bin/python3'`

## Check out the App in the Browser

Open this adress in your browser:

`<Remoteip>:<Port>`

For me it was the `192.168.178.43:3000`. It is a local adress.

## Stop AND remove the docker with the `stop_docker.yaml`

Use this command:

`python3 /home/<user>/.local/bin/ansible-playbook stop_docker.yaml -e 'ansible_python_interpreter=/usr/bin/python3'`
