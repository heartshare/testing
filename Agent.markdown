## SNMP Agent

```conf
# $Id: snmpd.conf 373 2010-02-16 13:31:41Z kai $
...
exec .1.3.6.1.4.1.7460.1.11 iptypestats /usr/xs4all/sbin/iptypestats
pass_persist .1.3.6.1.4.1.7460.1.12 /usr/xs4all/sbin/recursor-snmpd.pl
exec .1.3.6.1.4.1.7460.1.13 bind9stats /usr/xs4all/sbin/display-bind9stats.pl
exec .1.3.6.1.4.1.7460.1.14 postgresqlstats /usr/xs4all/sbin/postgresqlstats.pl
...
```


