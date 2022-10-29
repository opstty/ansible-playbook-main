# ansible-playbook-main

This Ansible playbook is a base for using differents ansible collections and roles effortlessly.

## Installation

### Retrieve the repository

Clone or download this repository to your local drive and change directory.

### Install preriquisites

- Add `$HOME/.local/bin` to your `$PATH`:

    ```console
    export $PATH="$PATH:$HOME/.local/bin"
    ```

- Upgrade Python3 pip:

    ```console
    sudo python3 -m pip install --upgrade pip
    ```

- Install Ansible and preriquisites:

    ```console
    python3 -m pip install --upgrade --user -r requirements.txt
    ```

### Setup sources directories

    ├── ...
    ├── requirements
    │   ├── playbook
    │   └── sources
    |   │   ├── ...
    |   │   ├── opstty
    |   |   │   ├── requirements.yml
    |   |   │   └── requirements.txt
    |   │   └── ...
    │   └── ...
    └── ...

- `opstty`: Ansible Galaxy namespace/GitHub Org;
- `requirements.yml`: Ansible Galaxy collections and roles;

    ```yaml
    ---
    collections:
    - opstty.k8s

    roles:
    - name: kubernetes
        src: https://github.com/opstty/ansible-role-kubernetes
        version: origin/master
    ```

- `requirements.txt`: Ansible Galaxy collections python requirements;

    ```console
    kubernetes-client==0.1.7
    ```

### Update the playbook

```console
ansible-playbook requirements/playbook/main.yml
```

If you want to enable `dev` mode, add `--extra-vars "git=true"`.

```console
ansible-playbook requirements/playbook/main.yml --extra-vars "git=true"
```

## Initialize a new role

### Prepare the playbook

Update the playbook in `dev` mode and change directory to `roles`.

```console
ansible-playbook requirements/playbook/main.yml --extra-vars "git=true"
cd roles
```

### Create the role

```console
ansible-galaxy init ansible-role-name --force
cd ansible-role-name
```

### (Optional): Initialize `molecule` new scenario

```console
molecule init scenario --role-name ansible-role-name
```

### (Optional): Adding a local repository to GitHub using Git

- Follow this [documentation](https://docs.github.com/en/get-started/importing-your-projects-to-github/importing-source-code-to-github/adding-locally-hosted-code-to-github#adding-a-local-repository-to-github-with-github-cli).

### (Optional): Retrieve the role using documentation

Follow thoses steps:

1. [Setup sources directories](README.md#setup-sources-directories)
2. [Update the playbook](README.md#update-the-playbook)  

## License

MIT / BSD

## Author Information

This role was created in 2022 by [Michael Hatoum](https://www.opstty.com/)
