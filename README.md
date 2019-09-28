# Himbert 🧸

Ansible setup for my personal Raspberry Pis.

## Getting Started

1. Install [`ansible`](https://www.ansible.com/)

        brew install ansible

1. Prepare Raspberry Pis

    1. [Download](https://www.raspberrypi.org/downloads/raspbian/) and [install](https://www.raspberrypi.org/documentation/installation/installing-images/mac.md) Raspbian Lite on Raspberry Pi

    1. [Enable ssh](https://www.raspberrypi.org/documentation/remote-access/ssh/) by placing an empty `ssh` file in the `boot` directory of the disk

    1. Add your ssh key to the Pi for password-less setup

            ssh-copy-id pi@raspberrypi.local

        *default password: `raspberry`*

1. Copy and adapt the *private* configuration:

        cp vars/private.yml.example vars/private.yml

## Running

1. Run core setup:

        bin/bootstrap

    _Note: this skips steps that need manual preparation (e.g. generating SSL certificates)._

1. Verify setup and perform manual setup steps (e.g. port forwarding on router)

1. Finalize setup

        bin/update


## Tips & Tricks

- edit file on a Pi as superuser:

        sudo -E vim <path-to-file>

    _(-E preserves the environment and keeps the configured vimrc)_
