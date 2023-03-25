# Himbert 🧸

Ansible setup for my personal Raspberry Pis.

Current raspberries:

| host             | pi  | connection | task                                                               |
| :--------------- | :-- | :--------- | :----------------------------------------------------------------- |
| **☁️  cloudbert** | 4   | LAN        | runs [Nextcloud](https://nextcloud.com/)                           |
| **💽 beatbert**  | 3b  | WIFI       | runs [Shairport-Sync](https://github.com/mikebrady/shairport-sync) |

## Getting Started 🎒

1. Install [`ansible`](https://www.ansible.com/)

   ```bash
   brew install ansible
   ```

1. Prepare Raspberry Pis

   1. Install [Raspberry Pi OS light](https://www.raspberrypi.com/software/)

   1. [Enable ssh](https://www.raspberrypi.org/documentation/remote-access/ssh/) by placing an empty `ssh` file in the `boot` directory of the disk

   1. _(optional)_ Plug an `ext4` formatted external harddrive into the Pi

   1. _(optional)_ [Configure WIFI](./DOC.md#set-up-wifi-for-a-pi) for the Pi

   1. Boot up your Pi _(and connect to LAN if necessary)_

   1. Add your ssh key to the Pi for password-less setup

      ```bash
      ssh-copy-id pi@raspberrypi.local
      ```

      _default password: `raspberry`_

1. Copy and adapt _host-specific_ configuration for every hosts:

   ```bash
   cp host_vars/hostname.yml.example host_vars/<hostname>.yml
   ```

## Running 🏃

1. Run core setup:

   ```bash
   script/setup
   ```

   _Note: this skips steps that need manual preparation (e.g. generating SSL certificates)._

1. Verify setup and perform manual setup steps (e.g. port forwarding on router)

1. Finalize setup

   ```bash
   script/update
   ```

## Tips & Tricks ⚙️

### Updating ✨

Run in _"check"_ mode first to see changes:

```bash
script/update --check
```

Alternatively, only run the check on certain groups or hosts, e.g.:

```bash
script/update --limit wifiberries --check

# or

script/update --limit beatbert --check
```

### Linting 💅

Use [ansible lint](https://docs.ansible.com/ansible-lint/) to check for bad practices in the playbook.

Install the CLI tool:

```bash
brew install ansible-lint

# probably needs linking
brew link ansible-lint
```

Run the linter on the playbook:

```bash
script/lint
```

See [docs](DOC.md) for some useful tips.
