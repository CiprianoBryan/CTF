# Discovery:

**1. ifconfig:**
```
root@kali:~# ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
		inet 192.168.1.3  netmask 255.255.255.0  broadcast 192.168.1.255
		inet6 fe80::20c:29ff:fe1e:282f  prefixlen 64  scopeid 0x20<link>
		ether 00:0c:29:1e:28:2f  txqueuelen 1000  (Ethernet)
		RX packets 60518  bytes 4021879 (3.8 MiB)
		RX errors 0  dropped 69  overruns 0  frame 0
		TX packets 36890  bytes 2221849 (2.1 MiB)
		TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
		inet 127.0.0.1  netmask 255.0.0.0
		inet6 ::1  prefixlen 128  scopeid 0x10<host>
		loop  txqueuelen 1000  (Local Loopback)
		RX packets 2008  bytes 84396 (82.4 KiB)
		RX errors 0  dropped 0  overruns 0  frame 0
		TX packets 2008  bytes 84396 (82.4 KiB)
		TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
````

**2.  nmap:**
```
root@kali:~# nmap 192.168.1.2-252
Starting Nmap 7.80 ( https://nmap.org ) at 2019-11-29 19:37 EST
Stats: 0:00:02 elapsed; 246 hosts completed (4 up), 4 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 25.31% done; ETC: 19:37 (0:00:03 remaining)
Nmap scan report for 192.168.1.10
Host is up (0.00056s latency).
Not shown: 997 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
3306/tcp open  mysql

Nmap scan report for 192.168.1.38
Host is up (0.024s latency).
All 1000 scanned ports on 192.168.1.38 are filtered

Nmap scan report for 192.168.1.46
Host is up (0.015s latency).
Not shown: 998 filtered ports
PORT     STATE SERVICE
2968/tcp open  enpp
5357/tcp open  wsdapi

Nmap scan report for 192.168.1.3
Host is up (0.0000070s latency).
All 1000 scanned ports on 192.168.1.3 are closed

Nmap done: 251 IP addresses (5 hosts up) scanned in 19.65 seconds
```

**3. nmap -A**
```
root@kali:~# nmap -A 192.168.1.10
Nmap scan report for 192.168.1.10
Host is up (0.0012s latency).
Not shown: 997 closed ports
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 7.4 (protocol 2.0)
| 	ssh-hostkey: 
|   	2048 c1:d3:be:39:42:9d:5c:b4:95:2c:5b:2e:20:59:0e:3a (RSA)
|   	256 43:4a:c6:10:e7:17:7d:a0:c0:c3:76:88:1d:43:a1:8c (ECDSA)
|_  	256 0e:cc:e3:e1:f7:87:73:a1:03:47:b9:e2:cf:1c:93:15 (ED25519)
80/tcp   open  http    Apache httpd 2.4.6 ((CentOS) PHP/5.4.16)
| 	http-methods: 
|_  	Potentially risky methods: TRACE
|_	http-server-header: Apache/2.4.6 (CentOS) PHP/5.4.16
|_	http-title: Apache HTTP Server Test Page powered by CentOS
3306/tcp open  mysql   MySQL 5.5.60-MariaDB
| 	mysql-info: 
|   	Protocol: 10
|   	Version: 5.5.60-MariaDB
|   	Thread ID: 4
|   	Capabilities flags: 63487
|   	Some Capabilities: IgnoreSigpipes, DontAllowDatabaseTableColumn, Support41Auth, ODBCClient, Speaks41ProtocolOld, FoundRows, LongColumnFlag, SupportsCompression, Speaks41ProtocolNew, ConnectWithDatabase, LongPassword, InteractiveClient, SupportsLoadDataLocal, SupportsTransactions, IgnoreSpaceBeforeParenthesis, SupportsMultipleStatments, SupportsAuthPlugins, SupportsMultipleResults
|   	Status: Autocommit
|   	Salt: ]aNCEq)r*t0,,:})Q={w
|_  	Auth Plugin Name: mysql_native_password
Device type: general purpose
Running: Linux 3.X|4.X
OS CPE: cpe:/o:linux:linux_kernel:3 cpe:/o:linux:linux_kernel:4
OS details: Linux 3.2 - 4.9
Network Distance: 1 hop

TRACEROUTE
HOP RTT       ADDRESS
1      1.24 ms 192.168.1.10

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 22.55 seconds
```