# splunk tech stack 

<img src="tech11.png">

### problem solved by Splunk 

<img src="prob1.png">

### splunk info 

<img src="spinfo.png">


## splunk components 

### search head 

<img src="shd.png">

### forwarder and Indexer 

<img src="spfi.png">

## a Visual look 

<img src="look.png">

### setup and Licensing 

<img src="setup.png">


### Installation of splunk Enterprise server with Free license 

### On linux Redhat platform 

```
[ec2-user@ip-172-31-60-129 ~]$ sudo -i
[root@ip-172-31-60-129 ~]# whoami
root

```

### download splunk enterserver software 

```
wget -O splunk-9.2.2-d76edf6f0a15.x86_64.rpm "https://download.splunk.com/products/splunk/releases/9.2.2/linux/splunk-9.2.2-d76edf6f0a15.x86_64.rpm"


====>>

--2024-07-08 07:01:24--  https://download.splunk.com/products/splunk/releases/9.2.2/linux/splunk-9.2.2-d76edf6f0a15.x86_64.rpm
Resolving download.splunk.com (download.splunk.com)... 18.154.227.97, 18.154.227.12, 18.154.227.35, ...
Connecting to download.splunk.com (download.splunk.com)|18.154.227.97|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 717684718 (684M) [binary/octet-stream]
Saving to: 'splunk-9.2.2-d76edf6f0a15.x86_64.rpm'

100%[=====================================================================================================>] 717,684,718 47.2MB/s   in 10s    

2024-07-08 07:01:34 (68.2 MB/s) - 'splunk-9.2.2-d76edf6f0a15.x86_64.rpm' saved [717684718/717684718]

===>>
[root@ip-172-31-60-129 ~]# ls
splunk-9.2.2-d76edf6f0a15.x86_64.rpm

```

### installing 

```
 rpm -ivh  splunk-9.2.2-d76edf6f0a15.x86_64.rpm 
warning: splunk-9.2.2-d76edf6f0a15.x86_64.rpm: Header V4 RSA/SHA256 Signature, key ID b3cd4420: NOKEY
Preparing...                          ################################# [100%]
Updating / installing...
   1:splunk-9.2.2-d76edf6f0a15        ################################# [100%]
complete

```

### verify 

```
rpm -qa | grep splunk
splunk-9.2.2-d76edf6f0a15.x86_64

OR 

rpm -q splunk 

splunk-9.2.2-d76edf6f0a15.x86_64


```

### Understanding configuration files of splunk server

```
cd  /opt/splunk/
[root@ip-172-31-60-129 splunk]# ls
LICENSE.txt        cmake          ftr      license-eula.txt  quarantined_files                                    swidtag
README-splunk.txt  copyright.txt  include  openssl           share
bin                etc            lib      opt               splunk-9.2.2-d76edf6f0a15-linux-2.6-x86_64-manifest


```

### configuration files 

```
/opt/splunk/

 cd  etc/
[root@ip-172-31-60-129 etc]# ls
anonymizer     deployment-apps      log-btool.cfg          log-utility.cfg  myinstall        searchLanguage.xml          splunk.version
apps           disabled-apps        log-cmdline-debug.cfg  log.cfg          openldap         shcluster                   system
auth           findlogs.ini         log-cmdline.cfg        manager-apps     packages         splunk-enttrial.lic         users
copyright.txt  init.d               log-debug.cfg          master-apps      packagetype      splunk-launch.conf
datetime.xml   log-btool-debug.cfg  log-searchprocess.cfg  modules          prettyprint.xsl  splunk-launch.conf.default


[root@ip-172-31-60-129 etc]# 

===>> verify splunk version 

cat  splunk.version 
VERSION=9.2.2
BUILD=d76edf6f0a15
PRODUCT=splunk
PLATFORM=Linux-x86_64


====> splunk main confi file is 

splunk-launch.conf


```

### a visual of splunk on Windows 

<img src="winsp.png">

### all Splunk bin commands are available at  bin directory 

```
 pwd
/opt/splunk/etc
[root@ip-172-31-60-129 etc]# cd  ..

[root@ip-172-31-60-129 splunk]# ls
LICENSE.txt        cmake          ftr      license-eula.txt  quarantined_files                                    swidtag
README-splunk.txt  copyright.txt  include  openssl           share
bin                etc            lib      opt               splunk-9.2.2-d76edf6f0a15-linux-2.6-x86_64-manifest


[root@ip-172-31-60-129 splunk]# ls  bin/
2to3-3.7                    genSignedServerCert.py         node                  pydoc3.7                        slim
ColdStorageArchiver.py      genSignedServerCert.sh         openssl               python                          spl-lang-server-sockets
ColdStorageArchiver_GCP.py  genWebCert.py                  parse_xml_buckets.py  python3                         spl2-orchestrator
S3benchmark                 genWebCert.sh                  pcre2-config          python3.7                       splunk
bloom                       idle3                          pcregextest           python3.7m                      splunk-optimize
bottle.py                   idle3.7                        pid_check.sh          pyvenv                          splunk-optimize-lex
btool                       importtool         
```

### starting splunk with license acceptance 

```
/opt/splunk/bin/splunk  start  --accept-license


This appears to be your first time running this version of Splunk.

Splunk software must create an administrator account during startup. Otherwise, you cannot log in.
Create credentials for the administrator account.
Characters do not appear on the screen when you type in credentials.

Please enter an administrator username: ashuadmin
Password must contain at least:
   * 8 total printable ASCII character(s).
Please enter a new password: 
Please confirm new password: 
Copying '/opt/splunk/etc/openldap/ldap.conf.default' to '/opt/splunk/etc/openldap/ldap.conf'.
Generating RSA private key, 2048 bit long modulu
```


### Now try to access splunk management console 

<img src="console1.png">

### splunk IP:8000 -- http://IP:8000 

### stopping and starting splunk service 

```
 /opt/splunk/bin/splunk  stop
Stopping splunkd...
Shutting down.  Please wait, as this may take a few minutes.
..                                                         [  OK  ]
Stopping splunk helpers...
                                                           [  OK  ]
Done.


[root@ip-172-31-60-129 splunk]# /opt/splunk/bin/splunk  start

Splunk> The Notorious B.I.G. D.A.T.A.

Checking prerequisites...
	Checking http port [8000]: open
	Checking mgmt port [8089]: open
	Checking appserver port [127.0.0.1:8065]: open

```

### splunk verify port details 

```
netstat -nlpt
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      2783/rpcbind        
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      3410/sshd           
tcp        0      0 0.0.0.0:8089            0.0.0.0:*               LISTEN      2823/splunkd        
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      3226/master         
tcp        0      0 0.0.0.0:8191            0.0.0.0:*               LISTEN      3053/mongod         
tcp        0      0 0.0.0.0:8000            0.0.0.0:*               LISTEN      2823/splunkd        
tcp        0      0 127.0.0.1:8065          0.0.0.0:*               LISTEN      3181/python3.7      
tcp6       0      0 :::111                  :::*                    LISTEN      2783/rpcbind        
tcp6       0      0 :::22                   :::*                    LISTEN      3410/sshd    
```

### to launch splunk server as docker contaienr 

<img src="spc1.png">


### make sure you have docker engine installed 

```
yum install docker -y  

 systemctl enable --now docker 
```

### lets creating docker container for splunk enterprise server 

```
docker  run  -itd --name ashusplunk  -p  1234:8000  -e "SPLUNK_START_ARGS=--accept-license" -e "SPLUNK_PASSWORD=Redhat@12345"  splunk/splunk:latest
```

### checking container status

```
docker  ps
CONTAINER ID   IMAGE                  COMMAND                  CREATED         STATUS                            PORTS                                                                                              NAMES
f4f046632b0b   splunk/splunk:latest   "/sbin/entrypoint.sh…"   9 seconds ago   Up 3 seconds (health: starting)   8065/tcp, 8088-8089/tcp, 8191/tcp, 9887/tcp, 9997/tcp, 0.0.0.0:1234->8000/tcp, :::1234->8000/tcp   ashusplunk
```

### lets stop contaienr and start original system process

```
 48  docker  stop ashusplunk
   49  docker  start ashusplunk
   50  docker  ps
   51  docker  stop  ashusplunk 
   52  history 
[root@ip-172-31-60-129 splunk]# /opt/splunk/bin/splunk  start

Splunk> The Notorious B.I.G. D.A.T.A.

Checking prerequisites...

```

## Indexer and indexes 

### Note : default index in splunk server is main 
<img src="main.png">

### creating index


### Understanding search process

<img src="SPL.png">

## SPL commands 

### searching in all indexed 

```
index=*
```

### searching on particular index 

```
index="security"
```

### splunk Distributed setup 

<img src="setup1.png">

### setup some sample app 

```
yum  install  git -y 

====>
Loaded plugins: extras_suggestions, langpacks, priorities, update-motd
Package git-2.40.1-1.amzn2.0.3.x86_64 already installed and latest version
Nothing to do

====>
[root@ip-172-31-93-203 ~]# git clone   https://github.com/schoolofdevops/html-sample-app.git
Cloning into 'html-sample-app'...
remote: Enumerating objects: 74, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 74 (delta 0), reused 0 (delta 0), pack-reused 71
Receiving objects: 100% (74/74), 1.38 MiB | 35.34 MiB/s, done.
Resolving deltas: 100% (5/5), done.
[root@ip-172-31-93-203 ~]# ls
html-sample-app
[root@ip-172-31-93-203 ~]# 




```

### to Host this webapp use apache httpd server 

```
yum install httpd -y 
==>
cp -rf html-sample-app/*   /var/www/html/

===>
systemctl  enable --now httpd
```

### type Splunk forwarder 

<img src="splunkf1.png">

### Downloading and setup Universal forwarder 

```
wget -O splunkforwarder-9.2.2-d76edf6f0a15.x86_64.rpm "https://download.splunk.com/products/universalforwarder/releases/9.2.2/linux/splunkforwarder-9.2.2-d76edf6f0a15.x86_64.rpm"

====>>
ls
html-sample-app  splunkforwarder-9.2.2-d76edf6f0a15.x86_64.rpm


[root@ip-172-31-93-203 ~]# rpm -ivh splunkforwarder-9.2.2-d76edf6f0a15.x86_64.rpm 
warning: splunkforwarder-9.2.2-d76edf6f0a15.x86_64.rpm: Header V4 RSA/SHA256 Signature, key ID b3cd4420: NOKEY
Preparing...                          ################################# [100%]
Updating / installing...
   1:splunkforwarder-9.2.2-d76edf6f0a1################################# [100%]
complete
[root@ip-172-31-93-203 ~]# 

===> default location of splunk forwarder 

 cd  /opt/splunkforwarder/
[root@ip-172-31-93-203 splunkforwarder]# ls
bin    copyright.txt  ftr      lib               LICENSE.txt  README-splunk.txt  splunkforwarder-9.2.2-d76edf6f0a15-linux-2.6-x86_64-manifest  uf
cmake  etc            include  license-eula.txt  openssl      share              swidtag
[root@ip-172-31-93-203 splunkforwarder]# 



```

### starting splunk forwarder 

```
/opt/splunkforwarder/bin/splunk   start  --accept-license 
Warning: Attempting to revert the SPLUNK_HOME ownership
Warning: Executing "chown -R splunkfwd:splunkfwd /opt/splunkforwarder"

This appears to be your first time running this version of Splunk.

Splunk software must create an administrator account during startup. Otherwise, you cannot log in.
Create credentials for the administrator account.
Characters do not appear on the screen when you type in credentials.

Please enter an administrator username: admin
Password must contain at least:
   * 8 total printable ASCII character(s).
Please enter a new password: 
Please confirm new password: 
Creating unit file...
```

### checking status 

```
/opt/splunkforwarder/bin/splunk  status
Warning: Attempting to revert the SPLUNK_HOME ownership
Warning: Executing "chown -R splunkfwd:splunkfwd /opt/splunkforwarder"
splunkd is running (PID: 1593).
splunk helpers are running (PIDs: 1628).
[root@ip-172-31-93-203 ~]# 


```

### adding indexer details to forwarder server 

```
 /opt/splunkforwarder/bin/splunk   add  forward-server   54.161.68.44:9997

 ====>>


 /opt/splunkforwarder/bin/splunk   list forward-server
Warning: Attempting to revert the SPLUNK_HOME ownership
Warning: Executing "chown -R splunkfwd:splunkfwd /opt/splunkforwarder"
Active forwards:
        None
Configured but inactive forwards:
        54.161.68.44:9997


```

### added data to splunk monitoring 


```
/opt/splunkforwarder/bin/splunk  add monitor   /var/log/httpd/
Warning: Attempting to revert the SPLUNK_HOME ownership
Warning: Executing "chown -R splunkfwd:splunkfwd /opt/splunkforwarder"
Added monitor of '/var/log/httpd'.
```

### restarting splunk forwarder service

```
 /opt/splunkforwarder/bin/splunk   restart
Warning: Attempting to revert the SPLUNK_HOME ownership
Warning: Executing "chown -R splunkfwd:splunkfwd /opt/splunkforwarder"
Stopping splunkd...
Shutting down.  Please wait, as this may take a few minutes.



```


