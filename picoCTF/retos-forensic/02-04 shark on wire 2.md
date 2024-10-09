## Objetivo
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/b506393b6f9d53b94011df000c534759/capture.pcap). Recover the flag that was pilfered from the network.
## Solución
- ##### Descargamos el archivo de captura de paquetes, y lo abriremos con el WireShark.
```
┌──(kali㉿kali)-[~/picoCTF/SharkOnWire2]
└─$ wget https://jupiter.challenges.picoctf.org/static/b506393b6f9d53b94011df000c534759/capture.pcap
--2024-10-08 23:31:01--  https://jupiter.challenges.picoctf.org/static/b506393b6f9d53b94011df000c534759/capture.pcap
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 112318 (110K) [application/octet-stream]
Saving to: ‘capture.pcap’

capture.pcap                 100%[============================================>] 109.69K  --.-KB/s    in 0.1s    

2024-10-08 23:31:02 (898 KB/s) - ‘capture.pcap’ saved [112318/112318]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/SharkOnWire2]
└─$ file capture.pcap
capture.pcap: pcap capture file, microsecond ts (little-endian) - version 2.4 (Ethernet, capture length 262144)
```

- ##### Una vez visto los paquetes, vemos que la bandera esta encriptada por medio del numero de puertos, por lo que realizaremos un script de Python.
``` bash
┌──(kali㉿kali)-[~/picoCTF/SharkOnWire2]
└─$ pipx install scapy       
⚠  Note: scapy was already on your PATH at /usr/bin/scapy
  installed package scapy 2.6.0, installed using Python 3.11.9
  These apps are now globally available
    - scapy
done! ✨ 🌟 ✨
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/SharkOnWire2]
└─$ nano exp.py          

from scapy.all import *

packets = rdpcap('capture.pcap')
flag = ''

for p in packets:
        if UDP in p and p[UDP].dport == 22:
                if p[UDP].sport > 5000:
                        flag += chr(p[UDP].sport - 5000)

print(flag)
 
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/SharkOnWire2]
└─$ python3 exp.py
picoCTF{p1LLf3r3d_data_v1a_st3g0}
```

- ##### Ejecutando el script, obtenemos la bandera.
```
Flag: picoCTF{p1LLf3r3d_data_v1a_st3g0}
```
## Notas Adicionales
- **PCAP** (Packet Capture) es un método para la captura, almacenamiento y análisis del tráfico de red.
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)