## Objetivo
This image passes LSB statistical analysis, but we can't help but think there must be something to the visual artifacts present in this image... Download the image [here](https://artifacts.picoctf.net/c/304/Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png)
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Forensics/MSB]
└─$ wget https://artifacts.picoctf.net/c/304/Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png
--2024-10-26 02:41:57--  https://artifacts.picoctf.net/c/304/Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.61, 3.161.55.26, 3.161.55.64, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.61|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3354311 (3.2M) [application/octet-stream]
Saving to: ‘Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png’

Ninja-and-Prince-Genji-Ukiyo 100%[============================================>]   3.20M  4.26MB/s    in 0.8s    

2024-10-26 02:41:58 (4.26 MB/s) - ‘Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png’ saved [3354311/3354311]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/MSB]
└─$ file Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png
Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png: PNG image data, 1074 x 1500, 8-bit/color RGB, non-interlaced
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/MSB]
└─$ open Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/MSB]
└─$ java -jar /opt/stegsolve.jar                           
Picked up _JAVA_OPTIONS: -Dawt.useSystemAAFontSettings=on -Dswing.aatext=true
```

- ##### Luego de extraer los datos mediante el "Stegsolver", obtenemos el archivo de texto plano.
```
┌──(kali㉿kali)-[~/picoCTF/Forensics/MSB]
└─$ ls
Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png  texto.txt

┌──(kali㉿kali)-[~/picoCTF/Forensics/MSB]
└─$ cat texto.txt | grep "picoCT"
picoCTF{15_y0ur_que57_qu1x071c_0r_h3r01c_ee3cb4d8}
```

- ##### Luego de hacer un grep, obtenemos la bandera.
```
Flag: picoCTF{15_y0ur_que57_qu1x071c_0r_h3r01c_ee3cb4d8}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)