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

