## Objetivo
Ron just found his own copy of advanced potion making, but its been corrupted by some kind of spell. Help him recover it!
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Forensics/advanced-potion-making]
└─$ wget https://artifacts.picoctf.net/picoMini+by+redpwn/Forensics/advanced-potion-making/advanced-potion-making
--2024-10-26 03:38:02--  https://artifacts.picoctf.net/picoMini+by+redpwn/Forensics/advanced-potion-making/advanced-potion-making
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.26, 3.161.55.100, 3.161.55.64, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.26|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 30372 (30K) [binary/octet-stream]
Saving to: ‘advanced-potion-making’

advanced-potion-making       100%[============================================>]  29.66K  --.-KB/s    in 0.05s   

2024-10-26 03:38:02 (648 KB/s) - ‘advanced-potion-making’ saved [30372/30372]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/advanced-potion-making]
└─$ file advanced-potion-making
advanced-potion-making: data
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/advanced-potion-making]
└─$ xxd advanced-potion-making | head                                 
00000000: 8950 4211 0d0a 1a0a 0012 1314 4948 4452  .PB.........IHDR
00000010: 0000 0990 0000 04d8 0802 0000 0004 2de7  ..............-.
00000020: 7800 0000 0173 5247 4200 aece 1ce9 0000  x....sRGB.......
00000030: 0004 6741 4d41 0000 b18f 0bfc 6105 0000  ..gAMA......a...
00000040: 0009 7048 5973 0000 1625 0000 1625 0149  ..pHYs...%...%.I
00000050: 5224 f000 0076 3949 4441 5478 5eec fd61  R$...v9IDATx^..a
00000060: 72e3 4c94 a659 ce16 6afe 76cd fe57 d7dd  r.L..Y..j.v..W..
00000070: 5b18 45e9 4b8a 7a28 d19d 2048 07a9 6376  [.E.K.z(.. H..cv
00000080: ac2d 2b3e bfaf 5f07 1801 82d7 b2f3 fff3  .-+>.._.........
00000090: fffc 7fff 7f00 0000 0000 0000 4b18 5802  ............K.X.
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/advanced-potion-making]
└─$ hexeditor -n advanced-potion-making
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/advanced-potion-making]
└─$ open advanced-potion-making
```

- ##### Al editar la imagen corrompida mediante el hexeditor, y luego aplicarle un filtro a blanco y negro, obtenemos la bandera.
```
Flag: picoCTF{w1z4rdry}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)