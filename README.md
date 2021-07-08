# Ansible Runner

Ansible runner allows you to run Ansible anywhere using Docker.

## Requirements

- Install [Docker](https://docs.docker.com/get-docker/).

## Installation

zsh (i.e. MacOS):

1. Create a file containing your zsh aliases by running this command:

    ````bash
    docker run -it --volume ${PWD}:/playbooks:rw --rm acrawly/ansible-runner:v2.10.4 ansible-playbook playbooks/install-zsh-alias.yml

2. After it completes, you'll have a file called `zshrc.txt` with the aliases you need to copy to the end of your `~/.zshrc` file. You can do that by running this command:

    ````bash
    cat zshrc.txt >> ~/.zshrc
    ````

3. Once done, reload your zsh configuration by running  

    ````bash
    source ~/.zshrc
    ````

powershell (i.e. Windows):

NOTE: If you want to use command prompt, use `%cd%` instead of `${pwd}`.

1. Create a file containing your alias by running:

    ```powershell
    docker run -it --volume ${pwd}:/playbooks:rw --rm acrawly/ansible-runner:latest ansible-playbook playbooks/install-ps-alias.yml
    ```

2. After the playbook executes, you'll have a file called 
You do NOT need to clone or download this repository, but these instructions assume you're working directory is the root of this directory.

Run the hello-world playbook:

`docker run -it --volume %cd%:/playbooks:ro --volume %userprofile%\.ssh:/root/.ssh:ro --rm acrawly/ansible-runner:v2.9.16 ansible --version`

`docker run -it --volume %cd%:/playbooks:ro --volume %userprofile%\.ssh:/root/.ssh:ro --rm acrawly/ansible-runner:latest ansible-playbook playbooks/hello-world.yml`

`docker run -it --volume "${PWD}":/playbooks:ro --volume ~/.ssh:/root/.ssh:ro --rm acrawly/ansible-runner:v2.9.16 ansible --version`

Edit Ansible Vault:

`docker run -it --volume "${PWD}":/playbooks:rw --volume ~/.ssh:/root/.ssh:ro --rm acrawly/ansible-runner:latest ansible-vault edit inventory/group_vars/all/vault`

View Ansible Vault:


## Making Aliases

`doskey aws=docker run --rm -it -v %userprofile%\.aws:/root/.aws -v %cd%:/aws amazon/aws-cli $*`


