# Lista de Pasos y Herramientas:

## 1. Reconocimiento:
```
nmap 192.168.1.2-254
```

## 2. Escaneo:
```
nmap -A 192.168.1.35
nmap --script vuln 192.168.1.35
```

## 3. Obtener acceso:
```
[Reverse Shell](https://ironhackers.es/herramientas/reverse-shell-cheat-sheet/)
**mysql** -h <ip> -u <user> -p
**ssh** <user>@<ip>
```

## 4. Mantener el acceso
## 5. Cubrir los pasos (Covering Tracks)