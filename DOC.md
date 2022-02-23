# Useful things along the way

## Format harddrive Ext4

Check where the drive is:

```bash
sudo fdisk -l
```

Go into `fdisk` and create the partition:

```bash
sudo fdisk /dev/sdb
```

Once you have the partition, format it:

```bash
sudo mkfs.ext4 /dev/sdb1
```

## Set up WIFI for a Pi

Enable the Pi to connect to your local WIFI directly on the first boot:

1. Generate encryped WIFI credentials on a Linux box via `wpa_passphrase`:

   ```
   wpa_passphrase "<network name>" "<password>"
   ```

1. Create a `wpa_supplicant.conf` file in the Pi's boot directory:

   ```bash
   vim /Volumes/boot/wpa_supplicant.conf
   ```

1. Put the generated network config into the new `wpa_supplicant.conf` file:

   ```conf
   ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
   update_config=1

   network={
    ssid="<network name>"
    psk="<password>"
   }
   ```

   _NOTE: you can also use a plaintext password and change it to an encrypted one later._

## Change the sound volume on the Pi

Use the [alsamixer](https://linux.die.net/man/1/alsamixer) tool:

```
alsamixer
```

## Edit file on Pi as superuser

`-E` preserves the environment and keeps the configured `vimrc`:

```bash
sudo -E vim <path-to-file>
```

## Nextcloud

Nextcloud specific tips & tricks.

### Run `occ` commands

In `nextcloud` directory:

```bash
sudo -u www-data php occ <command>
```
