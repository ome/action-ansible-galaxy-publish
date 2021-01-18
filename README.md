# Ansible Galaxy Publish GitHub action

A GitHub action to push an [Ansible](https://www.ansible.com/) role to [Ansible Galaxy](https://galaxy.ansible.com/).

This action requires Ansible 2.9+ to be pre-installed.
Ansible is included by default in the current GitHub workflow Ubuntu images, which means this action should run quickly since it does not need to install anything.

## Inputs

### `galaxy-api-key`

The Ansible Galaxy API key, required.

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
    runs-on: ubuntu-20.04
    steps:
      - name: galaxy
        uses: ome/action-ansible-galaxy-publish@main
        with:
          galaxy-api-key: ${{ secrets.GALAXY_API_KEY }}
```
