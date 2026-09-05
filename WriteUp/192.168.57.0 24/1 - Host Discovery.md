
Tengo acceso a esta red gracias a un pivoting desde la máquina FALL (192.168.56.4), por lo que todo el tráfico va tunelizado por proxychains.

Comando:

```bash
proxychains nmap -sT -Pn -T4 --open 192.168.57.0/24
```

Se utiliza `-sT` (TCP connect) en lugar de `-sS` (SYN scan) porque el tráfico atraviesa un proxy SOCKS mediante `proxychains`, que solo puede tunelizar conexiones TCP completas, no paquetes SYN "en crudo". Se añade `-Pn` porque el descubrimiento por ping (ICMP) tampoco se tuneliza correctamente a través del proxy, por lo que se asume que todos los hosts del rango están activos y se prueba conexión directa a los puertos.

Resultado:

```
Nmap scan report for 192.168.57.3
Host is up (0.035s latency).
Not shown: 989 filtered tcp ports (no-response), 4 closed tcp ports (conn-refused)
Some closed ports may be reported as filtered due to --defeat-rst-ratelimit
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
139/tcp  open  netbios-ssn
443/tcp  open  https
445/tcp  open  microsoft-ds
3306/tcp open  mysql
9090/tcp open  zeus-admin

Nmap scan report for 192.168.57.4
Host is up (0.035s latency).
Not shown: 999 closed tcp ports (conn-refused)
PORT   STATE SERVICE
80/tcp open  http
```

Conclusión:

La 192.168.57.3 es la máquina FALL, por lo que tenemos tan solo un objetivo en este rango de red, la 192.168.57.4