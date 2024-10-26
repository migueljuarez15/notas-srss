## Objetivo
The Network Operations Center (NOC) of your local institution picked up a suspicious file, they're getting conflicting information on what type of file it is. They've brought you in as an external expert to examine the file. Can you extract all the information from this strange file? Download the suspicious file [here](https://artifacts.picoctf.net/c_titan/7/flag2of2-final.pdf).
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Forensics/SecretOfThePloyglot]
└─$ wget https://artifacts.picoctf.net/c_titan/7/flag2of2-final.pdf
--2024-10-26 03:15:05--  https://artifacts.picoctf.net/c_titan/7/flag2of2-final.pdf
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.100, 3.161.55.26, 3.161.55.64, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.100|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3362 (3.3K) [application/octet-stream]
Saving to: ‘flag2of2-final.pdf’

flag2of2-final.pdf           100%[============================================>]   3.28K  --.-KB/s    in 0s      

2024-10-26 03:15:06 (84.0 MB/s) - ‘flag2of2-final.pdf’ saved [3362/3362]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/SecretOfThePloyglot]
└─$ file flag2of2-final.pdf                                     
flag2of2-final.pdf: PNG image data, 50 x 50, 8-bit/color RGBA, non-interlaced
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/SecretOfThePloyglot]
└─$ open flag2of2-final.pdf

1n_pn9_&_pdf_53b741d6}

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/SecretOfThePloyglot]
└─$ cp flag2of2-final.pdf imagen.png                            
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/SecretOfThePloyglot]
└─$ ls
flag2of2-final.pdf  imagen.png
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/SecretOfThePloyglot]
└─$ open imagen.png 

picoCTF{f1u3n7_
```

- ##### Al abrir los 2 archivos de diferentes formas "PNG y PDF", juntamos ambas partes y obtenemos la bandera.
```
Flag: picoCTF{f1u3n7_1n_pn9_&_pdf_53b741d6}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)