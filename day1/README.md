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
