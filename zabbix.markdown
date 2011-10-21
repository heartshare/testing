
### Zabbix

```shell
# Mysql "plugin"
UserParameter=mysql.ping,mysqladmin -uroot ping|grep alive|wc -l
UserParameter=mysql.uptime,mysqladmin -uroot status|cut -f2 -d":"|cut -f1 -d"T"
UserParameter=mysql.XXX,command-to-fillXXX
...

# Sensor "plugin"
UserParameter=sensor.temp4,sensors | grep "temp4" | awk '{ print $2+0 }'UserParameter=sensor.temp5,sensors | grep "temp5" | awk '{ print $2+0 }'
....

# Disk "plugin"
UserParameter = custom.vfs.dev.read.ops[*], cat /proc/diskstats | grep $1 | head -1 | awk '{ print $$4 }'
UserParameter = custom.vfs.dev.read.ms[*], cat /proc/diskstats | grep $1 | head -1 | awk '{ if ( $$8 ) print $$7 }'
...

# NFS "plugin"
UserParameter=nfs.getattr,cat /proc/net/rpc/nfs | grep -m 4 "proc3" | awk '{ print $4+0 }'
UserParameter=nfs.setattr,cat /proc/net/rpc/nfs | grep -m 4 "proc3" | awk '{ print $5+0 }'
...
```
