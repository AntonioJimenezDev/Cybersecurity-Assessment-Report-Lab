
La red a auditar comprende el rango de red 192.168.56.0/24, por lo que se realiza un escaneo de red con nmap para destapar los hosts activos.

Comando:

```bash
sudo nmap -sn 192.168.56.0/24
```

Resultado:

```
Nmap scan report for fedora.local (192.168.56.1)
Host is up (0.00022s latency).
MAC Address: 0A:00:27:00:00:00 (Unknown)
Nmap scan report for 192.168.56.2
Host is up (0.00024s latency).
MAC Address: 08:00:27:38:34:3A (Oracle VirtualBox virtual NIC)
Nmap scan report for 192.168.56.4
Host is up (0.00031s latency).
MAC Address: 08:00:27:7C:03:1C (Oracle VirtualBox virtual NIC)
Nmap scan report for 192.168.56.8
Host is up (0.00034s latency).
MAC Address: 08:00:27:22:23:03 (Oracle VirtualBox virtual NIC)
Nmap scan report for 192.168.56.5
Host is up.
```

Conclusión:

| IP           | Qué parece que es                                     |
| ------------ | ----------------------------------------------------- |
| 192.168.56.1 | Host anfitrión (fedora.local)                         |
| 192.168.56.2 | DHCP server interno de VirtualBox (no es un objetivo) |
| 192.168.56.4 | Máquina Objetivo                                      |
| 192.168.56.8 | Máquina Objetivo                                      |
| 192.168.56.5 | Máquina atacante                                      |
