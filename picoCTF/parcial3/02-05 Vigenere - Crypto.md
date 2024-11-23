## Objetivo
Can you decrypt this message? Decrypt this [message](https://artifacts.picoctf.net/c/160/cipher.txt) using this key "CYLAB".
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Crypto/Vigenere]
└─$ wget https://artifacts.picoctf.net/c/160/cipher.txt 
--2024-11-23 00:03:24--  https://artifacts.picoctf.net/c/160/cipher.txt
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.26, 3.161.55.61, 3.161.55.100, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.26|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 43 [application/octet-stream]
Saving to: ‘cipher.txt’

cipher.txt                   100%[============================================>]      43  --.-KB/s    in 0s      

2024-11-23 00:03:24 (73.1 MB/s) - ‘cipher.txt’ saved [43/43]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/Vigenere]
└─$ cat cipher.txt 
rgnoDVD{O0NU_WQ3_G1G3O3T3_A1AH3S_2951c89f}
```

- ##### Desencriptaremos el texto mediante Vigenere con la clave "CYLAB".
```
Texto Desencriptado:
rgnoDVD{O0NU_WQ3_G1G3O3T3_A1AH3S_2951c89f}

Clave:
CYLAB
```

- ##### Una vez desencriptado el texto, obtenemos la bandera.
```
Flag: picoCTF{D0NT_US3_V1G3N3R3_C1PH3R_2951a89h}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)