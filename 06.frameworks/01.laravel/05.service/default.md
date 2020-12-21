---
title: Service setup
---

A basic systemd service can be setup by creating a service file like this:
```bash
nano /etc/systemd/system/imap-idle.service
```
..and adding:
```bash
[Unit]
Description=ImapIdle
After=multi-user.target
After=syslog.target
After=network-online.target

[Service]
Type=simple

User=www-data
Group=www-data

WorkingDirectory=/var/www/my_project
ExecStart=/var/www/my_project/artisan fetch:idle

Restart=on-failure
RestartSec=5s

[Install]
WantedBy=multi-user.target
```

You can now test the service by running:
```bash
systemctl start imap-idle.service
systemctl status imap-idle.service
systemctl stop imap-idle.service
systemctl restart imap-idle.service
```
