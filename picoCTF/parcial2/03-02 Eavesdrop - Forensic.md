## Objetivo
Download this packet capture and find the flag.

- [Download packet capture](https://artifacts.picoctf.net/c/133/capture.flag.pcap)
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Forensics/Eavesdrop]
└─$ wget https://artifacts.picoctf.net/c/133/capture.flag.pcap                      
--2024-10-26 01:00:41--  https://artifacts.picoctf.net/c/133/capture.flag.pcap
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 13.225.222.105, 13.225.222.28, 13.225.222.120, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|13.225.222.105|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7518 (7.3K) [application/octet-stream]
Saving to: ‘capture.flag.pcap’

capture.flag.pcap            100%[============================================>]   7.34K  --.-KB/s    in 0s      

2024-10-26 01:00:42 (89.8 MB/s) - ‘capture.flag.pcap’ saved [7518/7518]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/Eavesdrop]
└─$ file capture.flag.pcap
capture.flag.pcap: pcap capture file, microsecond ts (little-endian) - version 2.4 (Ethernet, capture length 262144)
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/Eavesdrop]
└─$ wireshark capture.flag.pcap
                                                                                                          
┌──(kali㉿kali)-[~/picoCTF/Forensics/Eavesdrop]
└─$ ls          
capture.flag.pcap  file.des3
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/Eavesdrop]
└─$ openssl des3 -d -salt -in file.des3 -out file.txt -k supersecretpassword123
*** WARNING : deprecated key derivation used.
Using -iter or -pbkdf2 would be better.
bad decrypt
80E63825037F0000:error:1C800064:Provider routines:ossl_cipher_unpadblock:bad decrypt:../providers/implementations/ciphers/ciphercommon_block.c:107:
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/Eavesdrop]
└─$ cat file.txt      
N�^o箜5����&
59vk                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/Eavesdrop]
└─$ rm file.txt 
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/Eavesdrop]
└─$ openssl des3 -d -salt -in file.des3 -out file.txt -k supersecretpassword123
*** WARNING : deprecated key derivation used.
Using -iter or -pbkdf2 would be better.
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/Eavesdrop]
└─$ cat file.txt                                                               
picoCTF{nc_73115_411_5786acc3}
```

- ##### Después de exportar un texto proveniente del archivo ".pcap", para después desencriptarlo, obtenemos la bandera.
```
Flag: picoCTF{nc_73115_411_5786acc3}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)