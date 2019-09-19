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
