# Splunk With GenAI and GPT models 

<img src="splunkgpt.png">

### verify forwarder 

```
/opt/splunkforwarder/bin/splunk status

Warning: Attempting to revert the SPLUNK_HOME ownership
Warning: Executing "chown -R splunkfwd:splunkfwd /opt/splunkforwarder"
splunkd is running (PID: 3276).
splunk helpers are running (PIDs: 3345).

```

### verify httpd service 

```
systemctl status httpd 
● httpd.service - The Apache HTTP Server
   Loaded: loaded (/usr/lib/systemd/system/httpd.service; enabled; vendor preset: disabled)
   Active: active (running) since Thu 2024-07-11 02:27:35 UTC; 2h 23min ago
     Docs: man:httpd.service(8)
 Main PID: 3047 (httpd)
   Status: "Total requests: 14; Idle/Busy workers 100/0;Requests/sec: 0.00163; Bytes served/sec:   4 B/sec"
   Memory: 15.1M
   CGroup: /system.slice/httpd.service
           ├─3047 /usr/sbin/httpd -DFOREGROUND
           ├─3085 /usr/sbin/httpd -DFOREGROUND
           ├─3087 /usr/sbin/httpd -DFOREGROUND
```

### verify forwarder input config file 

```
/opt/splunkforwarder/bin/splunk list monitor
Warning: Attempting to revert the SPLUNK_HOME ownership
Warning: Executing "chown -R splunkfwd:splunkfwd /opt/splunkforwarder"
Your session is invalid.  Please login.
Splunk username: deepthidarisi
Password: 
Monitored Directories:

```

### splunk forwarder monitor input file 

```
cd  /opt/splunkforwarder/etc/apps/search/local
[root@ip-172-31-93-203 local]# ls
inputs.conf
[root@ip-172-31-93-203 local]# cat inputs.conf 
[monitor:///var/log/httpd]
disabled = false


[monitor:///var/log/secure]
disabled = false


```

### splunk dashboard is all about python libs -- 

<img src="pylib.png">

### task to  complete dashbaord creation 

<img src="dasht.png">

### alerts and notifications in Splunk Enterprise engine 

<img src="alert.png">


## Datastore and backup in Splunk 

### understading Indexer process 

<img src="index1.png">

### more closure look 

<img src="look1.png">

### understnading index in general 

<img src="store1.png">

### bucket location 

```
root@ip-172-31-60-129 splunk]# pwd
/opt/splunk/var/lib/splunk
[root@ip-172-31-60-129 splunk]# ls
audit           _configtracker.dat  _dsphonehome  _internal.dat       kvstore       _metrics_rollup    security.dat    weblogs
_audit.dat      defaultdb           fishbucket    _internaldb         main.dat      modinputs          summarydb       weblogs.dat
authDb          _dsappevent         hashDb        _introspection      _metrics      persistentstorage  _telemetry
_configtracker  _dsclient           historydb     _introspection.dat  _metrics.dat  security           _telemetry.dat
[root@ip-172-31-60-129 splunk]# cd weblogs/
[root@ip-172-31-60-129 weblogs]# ls
colddb  datamodel_summary  db  thaweddb
[root@ip-172-31-60-129 weblogs]# cd db/
[root@ip-172-31-60-129 db]# ls
CreationTime  db_1617819736_1617214936_0  GlobalMetaData
[root@ip-172-31-60-129 db]# cd ..
[root@ip-172-31-60-129 weblogs]# ls
colddb  datamodel_summary  db  thaweddb
[root@ip-172-31-60-129 weblogs]# cd ..
[root@ip-172-31-60-129 splunk]# ls
audit           _configtracker.dat  _dsphonehome  _internal.dat       kvstore       _metrics_rollup    security.dat    weblogs
_audit.dat      defaultdb           fishbucket    _internaldb         main.dat      modinputs          summarydb       weblogs.dat
authDb          _dsappevent         hashDb        _introspection      _metrics      persistentstorage  _telemetry
_configtracker  _dsclient           historydb     _introspection.dat  _metrics.dat  security           _telemetry.dat
[root@ip-172-31-60-129 splunk]# du -sh weblogs
6.2M    weblogs
[root@ip-172-31-60-129 splunk]# 

```

## setup of splunk server on Kubernetes 

### on kuberneres client 


```

kubectl   version --client 
Client Version: v1.28.8-eks-ae9a62a
Kustomize Version: v5.0.4-0.20230601165947-6ce0bf390ce3
[ec2-user@ip-172-31-82-122 ~]$ 
[ec2-user@ip-172-31-82-122 ~]$ 


[ec2-user@ip-172-31-82-122 ~]$ kubectl    get  nodes
NAME                                STATUS   ROLES   AGE    VERSION
aks-agentpool-84774012-vmss000000   Ready    agent   7h5m   v1.28.9
aks-agentpool-84774012-vmss000001   Ready    agent   7h5m   v1.28.9
[ec2-user@ip-172-31-82-122 ~]$ 

```

## stesp 

### creating namespace 

```
kubectl   get  ns
NAME              STATUS   AGE
default           Active   7h12m
kube-node-lease   Active   7h12m
kube-public       Active   7h12m
kube-system       Active   7h12m
[ec2-user@ip-172-31-82-122 ~]$ 
[ec2-user@ip-172-31-82-122 ~]$ kubectl    create   ns   ashu-splunk 
namespace/ashu-splunk created
[ec2-user@ip-172-31-82-122 ~]$ kubectl   get  ns
NAME              STATUS   AGE
ashu-splunk       Active   2s
default           Active   7h12m
kube-node-lease   Active   7h12m
kube-public       Active   7h12m
kube-system       Active   7h12m
[ec2-user@ip-172-31-82-122 ~]$ 

```

### creating deployment file 








