# Commands Glossary

<!-- mtoc-start -->

* [System Commands](#system-commands)
* [`cron` Commands](#cron-commands)
* [`ufw` Commands](#ufw-commands)
* [`sudo` Commands](#sudo-commands)
* [`ssh` Commands](#ssh-commands)

<!-- mtoc-end -->

## System Commands

- Switch user command, allows to run commands with another users privileges, by default the root user:
```sh
su
```

> [!Note]
> More on `su` command:
> - https://man7.org/linux/man-pages/man1/su.1.html
> - https://linuxize.com/post/su-command-in-linux/

___

- Control the systemd system and service manager:
```sh
systemctl
```

> [!Note]
> More on `systemctl` command:
> - https://www.commandlinux.com/man-page/man1/systemctl.1.html


- Shutdown the VM:
```sh
systemctl poweroff
```

- Reboot the VM
```sh
systemctl reboot
```

- Change `hostname`:
```sh
sudo hostnamectl set-hostname <hostname>
# And then change old user name to new one in:
sudo vim /etc/hosts
# and also
sudo vim /etc/hostname
# Reboot to apply changes
sudo reboot hostnamectl
```

> [!Note]
> More on `hostnamectl` command:
> - https://www.commandlinux.com/man-page/man1/systemctl.1.html


- Get system login password policy file:
```sh
sudo vim /etc/login.defs
```

> [!Note]
> More on `login.defs` file format and configuration:
> - https://man7.org/linux/man-pages/man5/login.defs.5.html

- Get user's password policy:
```sh
sudo vim /etc/pam.d/common-password
```

> [!Note]
> More on `PAM` configuration files:
> - https://www.man7.org/linux/man-pages/man5/pam.d.5.html

- Get system architecture:
```sh
uname -a
```

> [!Note]
> More on `uname` command:
> - https://man7.org/linux/man-pages/man1/uname.1.html

- Get cpu info:
```sh
sudo vim /proc/cpuinfo
```

> [!Note]
> More on `proc` file format:
> - https://man7.org/linux/man-pages/man5/proc.5.html

- Get memory info:
```sh
free
```

> [!Note]
> More on `free` command:
> - https://man7.org/linux/man-pages/man1/free.1.html
> - https://ioflood.com/blog/free-linux-command/

- Get disk info:
```sh
df
```

> [!Note]
> More on `df` command:
> - https://man7.org/linux/man-pages/man1/df.1.html

- Display processes:
```sh
top
# Or
vmstat
```

> [!Note]
> More on `top` command:
> - https://man7.org/linux/man-pages/man1/top.1.html
>
> More on `vmstat` command:
> - https://man7.org/linux/man-pages/man8/vmstat.8.html

- Get boot info:
```sh
who -b
# to get uptime in yyyy-mm-dd HH:MM:SS format
uptime -s
```

> [!Note]
> More on `who` command:
> - https://man7.org/linux/man-pages/man1/who.1.html
>
> More on `uptime` command:
> - https://man7.org/linux/man-pages/man1/uptime.1.html

- List information about all available block devices:
```sh
lsblk
```

> [!Note]
> More on `lsblk` command:
> - https://man7.org/linux/man-pages/man8/lsblk.8.html

- Check `users` information:
```sh
# print the user names of users currently logged in to the current host
users
# Show who is logged on and what they are doing.
w
```

> [!Note]
> More on `users` command:
> - https://man7.org/linux/man-pages/man1/users.1.html
>
> More on `w` command:
> - https://man7.org/linux/man-pages/man1/w.1.html

- Show routing, network devices, interfaces and tunnels:
```sh
ip --color a
# Or, specifically for interfaces
vim /etc/network/interfaces
```

> [!Note]
> More on `ip` command:
> - https://man7.org/linux/man-pages/man8/ip.8.html
>
> More on `/etc/network` file format:
> - https://man7.org/linux/man-pages/man5/networks.5.html

- Check all system sockets:
```sh
ss -tunlp
```

> [!Note]
> More on `ss` command:
> - https://man7.org/linux/man-pages/man8/ss.8.html


- Check if there is a `GUI` installed:
```sh
ls /usr/bin/*session
```

> [!Note]
> More on `session` file format:
> - https://www.linuxadictos.com/en/comprobar-existe-entorno-grafico-instalado-consola.html

___

## `cron` Commands

- Get system's `crontab`:
```sh
crontab -u root -e
```

- Stop `cron`:
```sh
sudo /etc/init.d/cron stop
```

- Start `cron`:
```sh
sudo /etc/init.d/cron start
```

> [!Note]
> More on `crontab` command:
> - https://man7.org/linux/man-pages/man1/crontab.1.html
>
> More on `crontab` file format:
> - https://man7.org/linux/man-pages/man5/crontab.5.html
>
> More on `cron` System Administration service:
> - https://man7.org/linux/man-pages/man8/cron.8.html

___

## `ufw` Commands

- Start `ufw`:
```sh
sudo ufw enable
```

- Stop `ufw`:
```sh
sudo ufw disable
```

- Get `ufw` status:
```sh
sudo ufw status
```

- Open a port:
```sh
sudo ufw allow <port>
```

- Close a port:
```sh
sudo ufw delete <port>
```

> [!Note]
> More on `ufw` command:
> - https://manpages.ubuntu.com/manpages/trusty/en/man8/ufw.8.html

___

## `sudo` Commands

- Run an interactive login shell with root user's environment:
```sh
sudo -i
```

> ![Note]
> - Is the same as running `su -`

- Check `sudo`'s version and other stats:
```sh
sudo -V
# or
dpkg -s sudo | grep Status
```

- Create a new user:
```sh
sudo adduser <username>
```

- Remove a user:
```sh
sudo deluser <username>
```

- Change a user's password:
```sh
sudo passwd <username>
```

- Create a new group:
```sh
sudo addgroup <groupname>
```

- Add a user to a group:
```sh
sudo adduser <username> <group>
```

- Get `PAM` password policy:
```sh
sudo vim /etc/pam.d/common-password
```

- Get `sudo_config` policy file:
```sh
sudo vim /etc/sudoers.d/sudo_config
```

- Get `sudo` log file:
```sh
sudo vim /var/log/sudo/sudo_config
```

- Get the system's journal
```sh
journalctl
```
___

## `ssh` Commands

- Get `hostname`:
```sh
hostname -I
```

- Connect to a remote host:
```sh
ssh -p <port> <username>@<hostname>
```

- Disconnect from a remote host:
```sh
exit
```

- Get `OpenSSH` server process config:
```sh
vim /etc/ssh/sshd_config
```

- Get `ssh` system-wide config:
```sh
vim /etc/ssh/ssh_config
```

- Restart the `OpenSSH` service:
```sh
sudo systemctl restart ssh
```

- Get `ssh` service status:
```sh
sudo service sshd status
```
