# Raspberry Pi Time Machine

If you're looking to set up a time machine on a raspberry pi with an external hard drive you've come to the right place.

## Setup

1. Set up your RPi OS and connect your external drive
2. Format the external drive

```sh
# Replace /dev/sda1 with what your disk comes up as
mkfs.ext4 /dev/sda1
mkdir /media/mount
```

3. Auto mount the drive by adding a line like this to `/etc/fstab`

```sh
/dev/sda1 /media/mount ext4 defaults,rw 0 0
```

4. Install docker and docker compose
5. Git clone this repo
6. Deploy this image

```sh
docker swarm init
# --resolve-image was to resolve a problem with the image not appearing to be the right architecture
docker stack deploy -c docker-compose.yml --resolve-image never samba
```
