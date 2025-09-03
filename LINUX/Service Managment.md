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
- hour (0-23)
- day of month (1-31)
- month of year (1-12)
- day of week (0-7) # 7 are Sunday
```

Examples:

```bash
1. Schedule a cron to execute at 2am daily  
    0 2 * * * /bin/sh backup.sh
2. Schedule a cron to execute twice a day  
    0 5,17 * * * /scripts/script.sh
3. Schedule a cron to execute on every minutes  
    * * * * *  /scripts/script.sh
4. Schedule a cron to execute on every Sunday at 5 PM  
    0 17 * * sun  /scripts/script.sh
5. Schedule a cron to execute on every 10 minutes  
    */10 * * * * /scripts/monitor.sh
6. Schedule a cron to execute on selected months  
    * * * jan,may,aug *  /script/script.sh
7. Schedule a cron to execute on selected days  
    0 17 * * sun,fri  /script/script.sh
8. Schedule a cron to execute on first sunday of every month  
    0 2 * * sun  [ $(date +%d) -le 07 ] && /script/script.sh
9. Schedule a cron to execute on every four hours  
    0 */4 * * * /scripts/script.sh
10. Schedule a cron to execute twice on every Sunday and Monday  
    0 4,17 * * sun,mon /scripts/script.sh
11. Schedule a cron to execute on every 30 Seconds  
    * * * * *  sleep 30; /scripts/script.sh
12. Schedule a multiple tasks in single cron  
    * * * * * /scripts/script.sh; /scripts/scrit2.sh
```



