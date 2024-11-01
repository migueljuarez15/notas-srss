## Objetivo
This service can provide you with a random number, but can it do anything else?
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Reversing/Picker1]
└─$ nc saturn.picoctf.net 57588
Try entering "getRandomNumber" without the double quotes...
==> getRandomNumber
4
Try entering "getRandomNumber" without the double quotes...
==> win
0x70 0x69 0x63 0x6f 0x43 0x54 0x46 0x7b 0x34 0x5f 0x64 0x31 0x34 0x6d 0x30 0x6e 0x64 0x5f 0x31 0x6e 0x5f 0x37 0x68 0x33 0x5f 0x72 0x30 0x75 0x67 0x68 0x5f 0x63 0x65 0x34 0x62 0x35 0x64 0x35 0x62 0x7d 
Try entering "getRandomNumber" without the double quotes...
==> ^C
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/Picker1]
└─$ python3       
Python 3.11.9 (main, Apr 10 2024, 13:16:36) [GCC 13.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> cadena = "0x70 0x69 0x63 0x6f 0x43 0x54 0x46 0x7b 0x34 0x5f 0x64 0x31 0x34 0x6d 0x30 0x6e 0x64 0x5f 0x31 0x6e 0x5f 0x37 0x68 0x33 0x5f 0x72 0x30 0x75 0x67 0x68 0x5f 0x63 0x65 0x34 0x62 0x35 0x64 0x35 0x62 0x7d".split()
>>> for char in cadena: print(chr(int(char, 16)), end = '')
... 
picoCTF{4_d14m0nd_1n_7h3_r0ugh_ce4b5d5b}
>>> exit()
```

- ##### Luego de poner la función "win" en el netcat, obtenemos un texto encriptado, y luego de desencriptarlo obtenemos la bandera.
```
Flag: picoCTF{4_d14m0nd_1n_7h3_r0ugh_ce4b5d5b}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)