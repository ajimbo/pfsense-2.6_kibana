### Ingesting Pfsense 2.6 data via logstash -> elasticsearch -> kibana

Pfsense 2.6
Logs:
1. "Firewall Events"
2. "DNS Events"

Log Format:
```
<134>Jun 17 13:37:58 filterlog[59716]: 130,,,1575729688,igb1,match,pass,in,4,0x0,,64,55831,0,DF,6,tcp,60,192.168.2.12,54.221.200.137,60293,443,0,S,3825784625,,29200,,mss;sackOK;TS;nop;wscale
```

Grok applied to Logstash to parse 5-tuple data and geoip for geo data

Result
```
{
  "protocol": "udp",
  "destination": {
    "port": "443",
    "ip": "10.10.10.1"
  },
  "action": "pass",
  "source": {
    "port": "54608",
    "ip": "192.168.2.117"
  }
}
```

### Check out visualization on Kibana Map fix
