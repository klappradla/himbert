# Himbert 🧸

Ansible setup for my personal Raspberry Pis.

_Opinionated setup for running [Nextcloud](https://nextcloud.com/) on a Raspberry Pi._

## Getting Started

1. Install [`ansible`](https://www.ansible.com/)

        brew install ansible

1. Prepare Raspberry Pis

    1. [Download](https://www.raspberrypi.org/downloads/raspbian/) and [install](https://www.raspberrypi.org/documentation/installation/installing-images/mac.md) Raspbian Lite on Raspberry Pi

    1. [Enable ssh](https://www.raspberrypi.org/documentation/remote-access/ssh/) by placing an empty `ssh` file in the `boot` directory of the disk

    1. Plug an `ext4` formatted external harddrive into the Pi

    1. Add your ssh key to the Pi for password-less setup

            ssh-copy-id pi@raspberrypi.local

        *default password: `raspberry`*

1. Copy and adapt _host-specific_ configuration for every hosts:

        cp host_vars/hostname.yml.example host_vars/<hostname>.yml

## Running

1. Run core setup:

        bin/bootstrap

    _Note: this skips steps that need manual preparation (e.g. generating SSL certificates)._

1. Verify setup and perform manual setup steps (e.g. port forwarding on router)

1. Finalize setup

        bin/update


## Tips & Tricks

### Updating

Run in _"check"_ mode first to see changes:

    bin/update --check

### Linting

Use [ansible lint](https://docs.ansible.com/ansible-lint/) to check for bad practices in the playbook.

Install the CLI tool:

    pip install ansible-lint

Run the linter on the playbook:

    ansible-lint base.yml

See [docs](DOC.md) for some useful tips.
