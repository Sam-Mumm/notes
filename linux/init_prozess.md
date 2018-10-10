# Init-Prozess unter Linux
## SysVinit
### Runlevel

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