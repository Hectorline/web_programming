Configuring Digital Ocean for simple droplet
============================================

Demo user already configured, it is forbidden to acces to root  user. Demo user has sudo privileges.

Now we are going to configure system time for use journald log.

See on DigitalOcean: \
https://www.digitalocean.com/community/tutorials/how-to-use-journalctl-to-view-and-manipulate-systemd-logs

```bash
timedatectl list-timezones
sudo timedatectl set-timezone Europe/Madrid
timedatectl status
```

To show all logs.

```bash
sudo journalctl [--utc]
```

To show current boot entries.

```bash
sudo journalctl -b
```

```bash
sudo mkdir -p /var/log/journal
```

```bash
sudo nano /etc/systemd/journald.conf
```

edit:

```txt

[Journal]
Storage=persistent

```

then:

```bash

sudo journalctl --list-boots

```

Managing systemd services and units
===================================

https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units

```bash

sudo systemctl list-units

```

```bash

sudo systemctl cat docker.socket
sudo systemctl show docker.socket

```

```txt

# /lib/systemd/system/docker.socket
[Unit]
Description=Docker Socket for the API
PartOf=docker.service

[Socket]
ListenStream=/var/run/docker.sock
SocketMode=0660
SocketUser=root
SocketGroup=docker

[Install]
WantedBy=sockets.target

```

Configure daemon.conf
=====================

(All images and containers will be removed using this.)

```bash

sudo nano /etc/docker/daemon.json

```

Add follow text:

```json
{
  "log-driver" : "journald",
  "storage-driver" : "overlay2"
}
```

then restart docker service:

```bash
sudo systemctl restart docker.service
```

