## Objetivo
How about some hide and seek heh? Look at this image [here](https://artifacts.picoctf.net/c/239/atbash.jpg).
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Crypto/HideToSee]
└─$ wget https://artifacts.picoctf.net/c/239/atbash.jpg 
--2024-10-23 13:41:06--  https://artifacts.picoctf.net/c/239/atbash.jpg
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.64, 3.161.55.100, 3.161.55.61, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.64|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 51504 (50K) [application/octet-stream]
Saving to: ‘atbash.jpg’

atbash.jpg                   100%[============================================>]  50.30K  --.-KB/s    in 0.06s   

2024-10-23 13:41:06 (796 KB/s) - ‘atbash.jpg’ saved [51504/51504]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/HideToSee]
└─$ steghide --extract -sf atbash.jpg
Enter passphrase: 
wrote extracted data to "encrypted.txt".
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/HideToSee]
└─$ cat encrypted.txt
krxlXGU{zgyzhs_xizxp_1u84w779}
```

- ##### Después de decodificar el ".txt", obtenemos la bandera.
```
Flag: picoCTF{atbash_crack_1f84d779}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)
- [CyberChef](https://gchq.github.io/CyberChef/)