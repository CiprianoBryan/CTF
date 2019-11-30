# Wireshark

## 1. Filtrar:
Ya que las maquinas no pueden conectarse significa que alguien
está haciendo desautenticación.
Por ello filtramos por [Deauthentication](https://github.com/CiprianoBryan/CTF/blob/master/Herramientas.md#wireshark)
```
> Frame 219111: 26 bytes on wire (208 bits), 26 bytes captured (208 bits)
v IEEE 802.11 Deauthentication, Flags: ........
    Type/Subtype: Deauthentication (0x000c)
    Frame Control Field: 0xc000
    .000 0001 0011 1010 = Duration: 314 microseconds
    Receiver address: Broadcast (ff:ff:ff:ff:ff:ff)
    Destination address: Broadcast (ff:ff:ff:ff:ff:ff)
    Transmitter address: AskeyCom_3b:b0:08 (08:6a:0a:3b:b0:08)
    Source address: AskeyCom_3b:b0:08 (08:6a:0a:3b:b0:08)
    BSS Id: AskeyCom_3b:b0:08 (08:6a:0a:3b:b0:08)
    .... .... .... 0000 = Fragment number: 0
    0000 0110 0011 .... = Sequence number: 99
> IEEE 802.11 wireless LAN
```

## 2. Explore:
Vemos que todos los paquetes fueron enviados por la misma maquina.
```
Source address: AskeyCom_3b:b0:08 (08:6a:0a:3b:b0:08)
```

## 3. CTF:
```
flag{08:6a:0a:3b:b0:08})
```