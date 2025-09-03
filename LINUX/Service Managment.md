## Init.d

**`init.d`** is a legacy system management used in Unix-like operating systems to manage services through shell scripts stored in the `/etc/init.d/` directory.

Basic syntax for the init.d system is:

/etc/init.d/**command** + **option**

**command**: there service name or script name
**option**: the operation to perform:
- start
- stop
- reload
- restart
- force-reload
## Systemd

**Systemd** is a modern system and service manager for Linux operating systems.

These files are placed in: 

- /usr/lib/systemd/system/ — Unit files provided by RPM-based packages (e.g., nginx, Apache, MySQL)
- /run/systemd/system/ — Unit files created at runtime
- /etc/systemd/system — user created Unit files

## Crond 

cron - daemon to execute scheduled commands.

Cron should be started from /etc/rc.d/init.d or /etc/init.d

```bash
* * * * * /path/to/script
  
- minute (0-59)
- ho
```


