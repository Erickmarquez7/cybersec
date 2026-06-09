# Reconocimiento

## Pasivo
No interactua directamente con el host

whois - Información sobre nombres de dominio
```bash
whois tryhackme.com
```

nslookup & dig - Consulta DNS, tipos de registro

```bash
nslookup -type=A tryhackme.com
nslookup -type=MX tryhackme.com 1.1.1.1
nslookup -type=TXT tryhackme.com
dig tryhackme.com A
dig @1.1.1.1 tryhackme.com MX
dig tryhackme.com TXT
```

DNSDumpster - Similar al anterior, permite subdominios

shodan.io - Dispositivos conectados a interner

censys.io - Similar

## Activo
Interactua directamente con el host

Navegador web - opciones de desarrollador: red, consola, recursos, aplicación, seguridad

ping - Prueba ICMP request (type 8) y ICMP reply (tipo 0)

| Resultado | Significado | Siguiente paso |
| ------ | ---- | ------ |
| Sin perdida   | Permite ICMP   | Escaneo de puertos |
| Host inalcanzable  | No existe o apagado   | Comprobar estado |
| Con pérdida  | Bloqueo o filtro   | Intentar con TCP/UDP   |
| Latencia alta  | Congestión, larga distancia   | traceroute   |

traceroute - Traza posibles caminos, envía 3 peticiones, puede cambiar el tipo de conexión TCP o UDP 

```bash
traceroute -T|-I MACHINE_IP
```

telnet - Realizar _''banner grabbing''_, obtener información gracias a los banner

```bash
telnet MACHINE_IP PORT
```

netcat - Realizar _''banner grabbing''_, similarmente
```bash
netcat MACHINE_IP PORT
```

O para escucha
```bash
netcat -nlvp PORT
```

Una vez elegido el cliente telnet, netcat, etc. entonces las peticiones dependen del protocolo