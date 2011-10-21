### Python code

```python
#!/usr/bin/python
"""Copyright Kai"""
import sys, time, os, subprocess, socket, re

CARBON_SERVER = '194.109.20.146'
CARBON_PORT = 2003
statsline = re.compile("^(\S*)\s+(\d*)$")

def get_stats():
    command = ('/usr/bin/rec_control', 'get-all')
    process = subprocess.Popen(command, stdout=subprocess.PIPE)
    addict={}
    for line in process.communicate()[0].split("\n"):
      r = re.match(statsline, line)
      if not r: continue
      addict[r.group(1)] = r.group(2)
    return addict

sock = socket.socket()
try:
  sock.connect( (CARBON_SERVER,CARBON_PORT) )
except:
  print "Error: Can't connect to %s:%d" % (CARBON_SERVER, CARBON_PORT)
  sys.exit(1)

now = int( time.time() )
hostname = os.uname()[1].split('.')[0]
lines = []
for k, v in get_stats().items():
  lines.append("dns.pdns.%s.%s %s %d\n" % (hostname, k, v, now))
message = ''.join(lines)
sock.sendall(message)
```
