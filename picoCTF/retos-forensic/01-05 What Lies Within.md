## Objetivo
There's something in the [building](https://jupiter.challenges.picoctf.org/static/011955b303f293d60c8116e6a4c5c84f/buildings.png). 
Can you retrieve the flag?
## Solución
- ##### Descargamos el archivo dado, y al observarlo, podemos apreciar que es una imagen, la cual usaremos la herramienta de Ruby "zsteg" para decodificarla.
```
┌──(kali㉿kali)-[~/picoCTF/WhatLiesWithin]
└─$ wget https://jupiter.challenges.picoctf.org/static/011955b303f293d60c8116e6a4c5c84f/buildings.png
--2024-10-03 05:17:25--  https://jupiter.challenges.picoctf.org/static/011955b303f293d60c8116e6a4c5c84f/buildings.png
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 625219 (611K) [application/octet-stream]
Saving to: ‘buildings.png’

buildings.png                100%[============================================>] 610.57K  1.73MB/s    in 0.3s    

2024-10-03 05:17:26 (1.73 MB/s) - ‘buildings.png’ saved [625219/625219]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/WhatLiesWithin]
└─$ ls
buildings.png
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/WhatLiesWithin]
└─$ file buildings.png
buildings.png: PNG image data, 657 x 438, 8-bit/color RGBA, non-interlaced
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/WhatLiesWithin]
└─$ zsteg -a buildings.png | grep "picoCTF"
b1,rgb,lsb,xy       .. text: "picoCTF{h1d1ng_1n_th3_b1t5}"

```

- ##### Luego de decodificar la imagen con la gema "zsteg", obtenemos la bandera.
```
Flag: picoCTF{h1d1ng_1n_th3_b1t5}
```
## Notas Adicionales
- **Steganography** is the practice of concealing information within another message or physical object to avoid detection. Steganography can be used to hide virtually any type of digital content, including text, image, video, or audio content. That hidden data is then extracted at its destination.
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)