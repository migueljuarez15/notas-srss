## Objetivo
I have these 2 images, can you make a flag out of them? [scrambled1.png](https://mercury.picoctf.net/static/49743139fb7c10765dbf462d40987d2a/scrambled1.png) [scrambled2.png](https://mercury.picoctf.net/static/49743139fb7c10765dbf462d40987d2a/scrambled2.png)
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Crypto/Pixelated]
└─$ wget https://mercury.picoctf.net/static/49743139fb7c10765dbf462d40987d2a/scrambled1.png
--2024-10-23 12:52:23--  https://mercury.picoctf.net/static/49743139fb7c10765dbf462d40987d2a/scrambled1.png
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 197173 (193K) [application/octet-stream]
Saving to: ‘scrambled1.png’

scrambled1.png               100%[============================================>] 192.55K  94.4KB/s    in 2.0s    

2024-10-23 12:52:26 (94.4 KB/s) - ‘scrambled1.png’ saved [197173/197173]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/Pixelated]
└─$ wget https://mercury.picoctf.net/static/49743139fb7c10765dbf462d40987d2a/scrambled2.png
--2024-10-23 12:52:37--  https://mercury.picoctf.net/static/49743139fb7c10765dbf462d40987d2a/scrambled2.png
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 197172 (193K) [application/octet-stream]
Saving to: ‘scrambled2.png’

scrambled2.png               100%[============================================>] 192.55K   160KB/s    in 1.2s    

2024-10-23 12:52:39 (160 KB/s) - ‘scrambled2.png’ saved [197172/197172]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/Pixelated]
└─$ file scrambled1.png              
scrambled1.png: PNG image data, 256 x 256, 8-bit/color RGB, non-interlaced
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/Pixelated]
└─$ file scrambled2.png
scrambled2.png: PNG image data, 256 x 256, 8-bit/color RGB, non-interlaced
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/Pixelated]
└─$ java -jar /opt/stegsolve.jar                   
Picked up _JAVA_OPTIONS: -Dawt.useSystemAAFontSettings=on -Dswing.aatext=true
```

- ##### Después de unir las dos imágenes por "ADD", obtenemos la bandera.
```
Flag: picoCTF{2a4d45c7}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)