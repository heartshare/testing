## Cricket config

### SNMP
```perl
# recursor stats
OID     questions               .1.3.6.1.4.1.7460.1.12.101.1
OID     tcp_questions           .1.3.6.1.4.1.7460.1.12.101.2
OID     cache_entries           .1.3.6.1.4.1.7460.1.12.101.3
...
```
### More duplications
```perl
# RRD definitions
dataSource questions            ds-source = snmp://%snmp%/questions
dataSource tcp_questions        ds-source = snmp://%snmp%/tcp_questions
dataSource cache_entries        
        ds-source = snmp://%snmp%/cache_entries
        rrd-ds-type     =       GAUGE
...
```
### Graph defines
```perl
# Graph definitions
graph questions
        legend = "questions"
        color = black

graph tcp_questions
        legend = "tcpquestions"

graph cache_entries
        legend = "cache entries"
        units = "entries"
...
```

### Visualize
```perl
# Targettype
targettype recursor-314-all
        ds = "questions, tcp_questions, cache_entries ..."
        view = "View: foo, bar, baz,
                Other: questions,
                TCP: tcp_questions cache_entries"
...
```


