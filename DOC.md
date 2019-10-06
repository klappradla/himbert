# Useful things along the way

## Format harddrive Ext4

Check where the drive is:

    sudo fdisk -l

Go into `fdisk` and create the partition:

    sudo fdisk /dev/sdb

Once you have the partition, format it:

    sudo mkfs.ext4 /dev/sdb1

## Edit file on Pi as superuser

`-E` preserves the environment and keeps the configured `vimrc`:

    sudo -E vim <path-to-file>
