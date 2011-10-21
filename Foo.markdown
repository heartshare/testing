## Cricket config

### SNMP

```perl
# recursor stats
OID     questions               .1.3.6.1.4.1.7460.1.12.101.1
OID     tcp_questions           .1.3.6.1.4.1.7460.1.12.101.2
OID     cache_entries           .1.3.6.1.4.1.7460.1.12.101.3
...
# Datasource
dataSource questions            ds-source = snmp://%snmp%/questions
dataSource tcp_questions        ds-source = snmp://%snmp%/tcp_questions
dataSource cache_entries        
        ds-source = snmp://%snmp%/cache_entries
        rrd-ds-type     =       GAUGE
...
```
