# [Red Hat / CentOS Check and List Running Services Linux Command]






## Red Hat / CentOS Check and List Running Services Command

Please note that systemd based system such as CentOS/RHEL 7.x/8.x and latest version of fedora use the systemctl command to list running services

### List running services using service command on a CentOS/RHEL 6.x or older

The syntax is as follows for CentOS/RHEL 6.x and older (pre systemd systems):
`service --status-allservice --status-all | moreservice --status-all | grep ntpdservice --status-all | less`

#### Print the status of any service

To print the status of apache (httpd) service:
`service httpd status`
Display status of sshd service:
`service sshd status`

#### List all known services (configured via SysV)

```
chkconfig --list
```

#### List service and their open ports

```
netstat -tulpn
```

#### Turn on / off service

`ntsysvchkconfig service offchkconfig service onchkconfig httpd offchkconfig ntpd on`
[ntsysv is a simple interface](https://www.cyberciti.biz/faq/rhel5-update-rcd-command/) for configuring runlevel services which are also configurable through chkconfig. By default, it configures the current runlevel. Just type ntsysv and select service you want to run.

## Red Hat / CentOS List Running Services using systemctl (RHEL/CentOS 7.x/8.x)

If you are using systemd based Linux distros such as Fedora Linux v22/23/24/26/27/28/29/30/31 or RHEL/CentOS Linux 7.x/8.x. Try the following command to list running services using the systemctl command. It control the systemd system and service manager.

### To list systemd services on CentOS/RHEL 7.x+ use

The syntax is:
`systemctlsystemctl | moresystemctl | grep httpdsystemctl list-units --type servicesystemctl list-units --type mount`
To list all services:
`systemctl list-unit-files`
Sample outputs:

![Fig.01: List all units installed on the CentOS /RHEL 7 systemd based system, along with their current states](https://www.cyberciti.biz/media/new/faq/2009/01/RHEL-CentOS-Redhat-7-list-runing-services.jpg)

Fig.01: List all units installed on the CentOS /RHEL 7 systemd based system, along with their current states

To view processes associated with a particular service (cgroup), you can use the systemd-cgtop command. Like the top command, systemd-cgtop lists running processes based on their service:
`systemd-cgtop`
Sample outputs:



```
Path                                            Tasks   %CPU   Memory  Input/s Output/s
 
/                                                  85    0.3   240.1M        -        -
/system.slice/NetworkManager.service                2      -        -        -        -
/system.slice/auditd.service                        1      -        -        -        -
/system.slice/crond.service                         1      -        -        -        -
/system.slice/dbus.service                          1      -        -        -        -
/system.slice/lvm2-lvmetad.service                  1      -        -        -        -
/system.slice/polkit.service                        1      -        -        -        -
/system.slice/postfix.service                       3      -        -        -        -
/system.slice/rsyslog.service                       1      -        -        -        -
/system.slice/sshd.service                          1      -        -        -        -
/system.slice/...tty.slice/getty@tty1.service       1      -        -        -        -
/system.slice/systemd-journald.service              1      -        -        -        -
/system.slice/systemd-logind.service                1      -        -        -        -
/system.slice/systemd-udevd.service                 1      -        -        -        -
/system.slice/tuned.service                         1      -        -        -        -
/system.slice/wpa_supplicant.service                1      -        -        -        -
/user.slice/user-0.slice/session-2.scope            1      -        -        -        -
/user.slice/user-1000.slice/session-1.scope         4      -        -        -        -
```

### To list SysV services only on CentOS/RHEL 7.x+ use (does not include native systemd services)

`chkconfig --list`
Sample outputs:

![Fig.02: List Sysv based services on systemd](https://www.cyberciti.biz/media/new/faq/2009/01/checkconfig-list.jpg)

Fig.02: List Sysv based services on systemd

### How to check the status of a service using systemd

Say you want to check status of a service named sshd, run
`$ systemctl status sshd.service`
Sample outputs:

```
<span style='color: rgb(0, 153, 0);'>●</span> ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: enabled)
     Active: <span style='color: rgb(0, 153, 0);'>active (running)</span> since Tue 2020-08-04 06:15:53 IST; 17h ago
       Docs: man:sshd(8)
             man:sshd_config(5)
    Process: 3180 ExecStartPre=/usr/sbin/sshd -t (code=exited, status=0/SUCCESS)
   Main PID: 3236 (sshd)
      Tasks: 1 (limit: 37952)
     Memory: 2.6M
     CGroup: /system.slice/ssh.service
             └─3236 sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups
 
Warning: journal has been rotated since unit was started, output may be incomplete.
```

#### Verifying the status of a service

One can verify that if a service named sshd is running (active) or not running (inactive) on a CentOS/RHEL 7.x+:
`systemctl is-active sshdsystemctl is-enabled sshdsystemctl is-active nginxsystemctl is-enabled nginxsystemctl is-enabled httpd`
![Check whether a service is running or not running on a CentOS RHEL](https://www.cyberciti.biz/media/new/faq/2009/01/Check-whether-a-service-is-running-or-not-running-on-a-CentOS-RHEL.png)

### Listing RHEL/CentOS 8.x services

We use the following command to find about currently loaded services:
`$ sudo systemctl list-units --type=service`

```
UNIT                               LOAD   ACTIVE SUB     DESCRIPTION                           
_____________________________________________________________________________________________________
console-getty.service              loaded active running Console Getty                         
crond.service                      loaded active running Command Scheduler                     
dbus.service                       loaded active running D-Bus System Message Bus              
dracut-shutdown.service            loaded active exited  Restore /run/initramfs on shutdown    
NetworkManager-wait-online.service loaded active exited  Network Manager Wait Online           
NetworkManager.service             loaded active running Network Manager                       
rsyslog.service                    loaded active running System Logging Service                
systemd-journal-flush.service      loaded active exited  Flush Journal to Persistent Storage   
systemd-journald.service           loaded active running Journal Service                       
systemd-logind.service             loaded active running Login Service                         
systemd-resolved.service           loaded active running Network Name Resolution               
systemd-sysctl.service             loaded active exited  Apply Kernel Variables                
systemd-tmpfiles-setup-dev.service loaded active exited  Create Static Device Nodes in /dev    
systemd-tmpfiles-setup.service     loaded active exited  Create Volatile Files and Directories 
systemd-udev-trigger.service       loaded active exited  udev Coldplug all Devices             
systemd-udevd.service              loaded active running udev Kernel Device Manager            
systemd-update-utmp.service        loaded active exited  Update UTMP about System Boot/Shutdown
systemd-user-sessions.service      loaded active exited  Permit User Sessions                  
 
LOAD   = Reflects whether the unit definition was properly loaded.
ACTIVE = The high-level unit activation state, i.e. generalization of SUB.
SUB    = The low-level unit activation state, values depend on unit type.
 
18 loaded units listed. Pass --all to see loaded but inactive units, too.
To show all installed unit files use 'systemctl list-unit-files'.
```

Type systemctl command without any options to show both loaded and active units/services:
`$ sudo systemctl`
Filter out using the [grep command](https://www.cyberciti.biz/faq/howto-use-grep-command-in-linux-unix/)/[egrep command](https://www.cyberciti.biz/faq/grep-regular-expressions/):
`$ sudo systemct | egerep 'httpd|php-fpm|mysqld|nginx'$ sudo systemctl list-units --type=service | grep nginx`

### Listing service/unit dependencies

The syntax is:
`# systemctl list-dependencies {service-name}# systemctl list-dependencies nginx.service# systemctl list-dependencies php-fpm.service# systemctl list-dependencies sshd.service# systemctl list-dependencies crond.service`

```
crond.service
● ├─system.slice
● └─sysinit.target
●   ├─dev-hugepages.mount
●   ├─dev-mqueue.mount
●   ├─dracut-shutdown.service
●   ├─import-state.service
●   ├─kmod-static-nodes.service
●   ├─ldconfig.service
●   ├─loadmodules.service
●   ├─proc-sys-fs-binfmt_misc.automount
●   ├─selinux-autorelabel-mark.service
●   ├─sys-fs-fuse-connections.mount
●   ├─sys-kernel-config.mount
●   ├─sys-kernel-debug.mount
●   ├─systemd-ask-password-console.path
●   ├─systemd-binfmt.service
●   ├─systemd-firstboot.service
●   ├─systemd-hwdb-update.service
●   ├─systemd-journal-catalog-update.service
●   ├─systemd-journal-flush.service
●   ├─systemd-journald.service
●   ├─systemd-machine-id-commit.service
●   ├─systemd-modules-load.service
●   ├─systemd-random-seed.service
●   ├─systemd-sysctl.service
●   ├─systemd-sysusers.service
●   ├─systemd-tmpfiles-setup-dev.service
●   ├─systemd-tmpfiles-setup.service
●   ├─systemd-udev-trigger.service
●   ├─systemd-udevd.service
●   ├─systemd-update-done.service
●   ├─systemd-update-utmp.service
●   ├─cryptsetup.target
●   ├─local-fs.target
●   │ └─systemd-remount-fs.service
●   └─swap.target
```

## Conclusion

For latest version of the CentOS/RHEL 7.x use the systemctl command and for older version try [service command](https://bash.cyberciti.biz/guide/Service_command) to show all services running under Centos or RHEL Server.

