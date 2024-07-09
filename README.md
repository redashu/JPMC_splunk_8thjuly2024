## Participants tech backgroud 

<img src="tech.png">

### labs understanding 

<img src="labs.png">



### timings session splunk

<img src="time.png">

### Regex token & keywords 

<img src="token.png">

## giving a name to group 

```
^(?<myclientIP>\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3})
```

### using regex in splunk  SPL 

```
index="main" host="ip-172-31-93-203.ec2.internal" | regex _raw="\b(400|404|408|402)\b" | stats count by clientip | where count < 5
```

### checking client IP with Rex 

```
index="main" host="ip-172-31-93-203.ec2.internal" (status=404 OR status=400 OR status=408) | rex field=_raw "^(?<myclientIP>\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3})" | stats count by myclientIP | rename count as "http_400_range_events" | sort - http_400_range_events
```

### another way 

```
index="main" host="ip-172-31-95-77.ec2.internal" | rex field=_raw "^(?P<myclientsIP>\d+\.\d+\.\d+\.\d+)" | stats count by myclientsIP
```

### matching more specific data 

```
index="main" host="ip-172-31-93-203.ec2.internal" (status=404 OR status=400 OR status=408)
| rex field=_raw "^(?<myclientIP>\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}) - - \[.*\] \"GET (?<page>.*?) HTTP/\d\.\d\""
| stats count by myclientIP, page
```
