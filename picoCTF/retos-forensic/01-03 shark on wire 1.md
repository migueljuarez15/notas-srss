## Objetivo
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/483e50268fe7e015c49caf51a69063d0/capture.pcap). Recover the flag.
## Solución
- ##### Descargaremos el archivo que se nos da, y observándolo, vemos que es un archivo ".pcap". Abriremos el archivo mediante "Wireshark".
```
┌──(kali㉿kali)-[~/picoCTF/SharkOnWire1]
└─$ wget https://jupiter.challenges.picoctf.org/static/483e50268fe7e015c49caf51a69063d0/capture.pcap
--2024-10-03 03:28:44--  https://jupiter.challenges.picoctf.org/static/483e50268fe7e015c49caf51a69063d0/capture.pcap
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 239455 (234K) [application/octet-stream]
Saving to: ‘capture.pcap’

capture.pcap                 100%[============================================>] 233.84K  1.14MB/s    in 0.2s    

2024-10-03 03:28:45 (1.14 MB/s) - ‘capture.pcap’ saved [239455/239455]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/SharkOnWire1]
└─$ file capture.pcap
capture.pcap: pcap capture file, microsecond ts (little-endian) - version 2.4 (Ethernet, capture length 262144)
```

- ##### Con lo siguiente, le daremos a la opción "Follow", y navegaremos por los stream UDP.
```
11	37.894161	10.0.0.9	10.0.0.5	UDP	66	5000 → 8990 Len=24
```

- ##### Una vez navegando por los streams, hallaremos la bandera.
```
Flag: picoCTF{StaT31355_636f6e6e}
```
## Notas Adicionales
- **PCAP** (Packet Capture) es un método para la captura, almacenamiento y análisis del tráfico de red.
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)