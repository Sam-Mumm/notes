# Init-Prozess unter Linux
## SysVinit
### Runlevel bei Linux

| Runlevel | Beschreibung |
| --- | --- |
| 0 | Shutdown |
| 1 | Einzelnutzerbetrieb ohne Netzwerk |
| 2 | lokaler Mehrbenutzerbetrieb ohne Netzwerk |
| 3 | Netzwerk steht zur Verfügung, **ohne** GUI |
| 4 | nicht definiert |
| 5 | Netzwerk steht zur Verfügung, **mit** GUI |
| 6 | Reboot |

### minimales Bootscript
```
#!/bin/ksh
#
# /etc/init.d/[Scriptname]
#
### BEGIN INIT INFO
# Provides: [Applicationname]
# Required-Start: $network
# Required-Stop:
# Default-Start:  2 3 5
# Default-Stop:   0 1 6
# Short-Description: Startet den [Applicationname]
# Description: Startet den [Applicationname]
### END INIT INFO

case "$1" in
		start)
				echo "Start of [Applicationname]"
				cd /path/to/app/dir
				./script.sh start 2>&1
		;;
		stop)
				echo "Stopping of [Applicationname]"
				cd /path/to/app/dir
				./script.sh stop 2>&1
		;;
		*)
				echo "Usage: $0 start|stop";;
esac
```

## systemd
```
[Unit]
Description=Description of the tool
After=network.target network-online.target mysql.service
Wants=network-online.target

[Service]
ExecStart=/path/to/dir/to/start/the/app
ExecStop=/path/to/dir/to/stop/the/app
ExecReload=/path/to/dir/to/restart/the/app
PIDFile=/path/to/pid/file
Type=forking
User=user

[Install]
WantedBy=multi-user.target
```
