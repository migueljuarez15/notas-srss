## Objetivo
This [garden](https://jupiter.challenges.picoctf.org/static/4153422e18d40363e7ffc7e15a108683/garden.jpg) contains more than it seems.
## Solución
- ##### Descargaremos la imagen que se nos da, y después de ver el tipo de archivo y observar la imagen, vamos a abrirla mediante el "hexeditor"
```
┌──(kali㉿kali)-[~/picoCTF/GloryOfTheGarden]
└─$ wget https://jupiter.challenges.picoctf.org/static/4153422e18d40363e7ffc7e15a108683/garden.jpg
--2024-10-03 00:21:41--  https://jupiter.challenges.picoctf.org/static/4153422e18d40363e7ffc7e15a108683/garden.jpg
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2295192 (2.2M) [application/octet-stream]
Saving to: ‘garden.jpg’

garden.jpg                   100%[============================================>]   2.19M  3.52MB/s    in 0.6s    

2024-10-03 00:21:42 (3.52 MB/s) - ‘garden.jpg’ saved [2295192/2295192]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/GloryOfTheGarden]
└─$ ls                     
garden.jpg
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/GloryOfTheGarden]
└─$ file garden.jpg                                                            
garden.jpg: JPEG image data, JFIF standard 1.01, resolution (DPI), density 72x72, segment length 16, baseline, precision 8, 2999x2249, components 3
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/GloryOfTheGarden]
└─$ open garden.jpg
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/GloryOfTheGarden]
└─$ hexeditor garden.jpg
```

- ##### Una vez en el "hexeditor", observamos que son una gran cantidad de información guardada, buscar la bandera manual sería muy difícil.
```
File: garden.jpg                                                    ASCII Offset: 0x00000000 / 0x00230597 (%00)   
00000000  FF D8 FF E0  00 10 4A 46   49 46 00 01  01 01 00 48                                     ......JFIF.....H
00000010  00 48 00 00  FF E2 0C 58   49 43 43 5F  50 52 4F 46                                     .H.....XICC_PROF
00000020  49 4C 45 00  01 01 00 00   0C 48 4C 69  6E 6F 02 10                                     ILE......HLino..
00000030  00 00 6D 6E  74 72 52 47   42 20 58 59  5A 20 07 CE                                     ..mntrRGB XYZ ..
e   t   c   .   .   .
```

- ##### En el "hexeditor", buscaremos la palabra "picoCTF" para obtener la bandera.
```
Flag: picoCTF{more_than_m33ts_the_3y33dd2eEF5}
```
## Notas Adicionales
- Un **editor hexadecimal** es un tipo de programa informático que permite a un usuario modificar archivos binarios. Los editores hexadecimales fueron diseñados para editar sectores de datos de disquetes o discos duros por lo que a veces se llaman "editores de sectores".
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)