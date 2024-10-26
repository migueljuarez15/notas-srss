## Objetivo
Download the packet capture file and use packet analysis software to find the flag.

- [Download packet capture](https://artifacts.picoctf.net/c/194/network-dump.flag.pcap)
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Forensics/PacketsPrimer]
└─$ wget https://artifacts.picoctf.net/c/194/network-dump.flag.pcap                                 
--2024-10-26 03:04:57--  https://artifacts.picoctf.net/c/194/network-dump.flag.pcap
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.26, 3.161.55.100, 3.161.55.64, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.26|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 778 [application/octet-stream]
Saving to: ‘network-dump.flag.pcap’

network-dump.flag.pcap       100%[============================================>]     778  --.-KB/s    in 0s      

2024-10-26 03:04:58 (25.6 MB/s) - ‘network-dump.flag.pcap’ saved [778/778]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/PacketsPrimer]
└─$ wireshark network-dump.flag.pcap 
```

- ##### Al seguir el stream de paquetes TCP, obtenemos la bandera.
```
Flag: picoCTF{p4ck37_5h4rk_ceccaa7f}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)