# Ansible Galaxy Publish GitHub action

A GitHub action to push an [Ansible](https://www.ansible.com/) role to [Ansible Galaxy](https://galaxy.ansible.com/).

This action requires Ansible 2.9+ to be pre-installed.
Ansible is included by default in the current GitHub workflow Ubuntu images, which means this action should run quickly since it does not need to install anything.

## Inputs

### `galaxy-api-key`

The Ansible Galaxy API key, required.

### `galaxy-version`

The version to push to Ansible galaxy, required. e.g. 0.4.0

### role-name
The name of the role. The value in ``meta/main.yml` is not taken into account when using the url

## Example usage

Here is a default configuration.
Note it is not necessary to checkout the repository 😀, only the repository owner and name are required and these are obtained from the environment.

```yaml
---
on:
  push:
    tags:

jobs:
  build:
    runs-on: ubuntu-22.04
    steps:
      - name: galaxy
        uses: ome/action-ansible-galaxy-publish@main
        with:
          galaxy-api-key: ${{ secrets.GALAXY_API_KEY }}
          galaxy-version: ${{  github.ref_name }}
          role-name: ${{ steps.role-name.outputs.rolename }}
```

The role name is usually read from the ``meta/main.yml` file.
