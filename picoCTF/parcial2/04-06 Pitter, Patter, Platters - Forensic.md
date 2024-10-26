## Objetivo
'Suspicious' is written all over this disk image. Download [suspicious.dd.sda1](https://jupiter.challenges.picoctf.org/static/52f3ab2c16c051e744ea5b029c24011b/suspicious.dd.sda1)
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Forensics/PitterPatterPlatters]
└─$ wget https://jupiter.challenges.picoctf.org/static/52f3ab2c16c051e744ea5b029c24011b/suspicious.dd.sda1
--2024-10-26 04:02:03--  https://jupiter.challenges.picoctf.org/static/52f3ab2c16c051e744ea5b029c24011b/suspicious.dd.sda1
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 32868864 (31M) [application/octet-stream]
Saving to: ‘suspicious.dd.sda1’

suspicious.dd.sda1           100%[============================================>]  31.35M  6.43MB/s    in 5.4s    

2024-10-26 04:02:09 (5.78 MB/s) - ‘suspicious.dd.sda1’ saved [32868864/32868864]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/PitterPatterPlatters]
└─$ file suspicious.dd.sda1
suspicious.dd.sda1: Linux rev 1.0 ext3 filesystem data, UUID=fc168af0-183b-4e53-bdf3-9c1055413b40 (needs journal recovery)
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/PitterPatterPlatters]
└─$ fls suspicious.dd.sda1           
d/d 11: lost+found
d/d 2009:       boot
d/d 4017:       tce
r/r 12: suspicious-file.txt
V/V 8033:       $OrphanFiles
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/PitterPatterPlatters]
└─$ icat suspicious.dd.sda1 12                 
Nothing to see here! But you may want to look here -->
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/PitterPatterPlatters]
└─$ xxd -s 0x200400 -l 200 suspicious.dd.sda1
00200400: 4e6f 7468 696e 6720 746f 2073 6565 2068  Nothing to see h
00200410: 6572 6521 2042 7574 2079 6f75 206d 6179  ere! But you may
00200420: 2077 616e 7420 746f 206c 6f6f 6b20 6865   want to look he
00200430: 7265 202d 2d3e 0a7d 0031 0032 0039 0030  re -->.}.1.2.9.0
00200440: 0038 0038 0061 0062 005f 0033 003c 005f  .8.8.a.b._.3.<._
00200450: 007c 004c 006d 005f 0031 0031 0031 0074  .|.L.m._.1.1.1.t
00200460: 0035 005f 0033 0062 007b 0046 0054 0043  .5._.3.b.{.F.T.C
00200470: 006f 0063 0069 0070 0000 0000 0000 0000  .o.c.i.p........
00200480: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00200490: 0000 0000 0000 0000 0000 0000 0000 0000  ................
002004a0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
002004b0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
002004c0: 0000 0000 0000 0000                      ........
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/PitterPatterPlatters]
└─$ echo picoCTF{b3_5t111_mL|_<3_ba880921}
```

- ##### Después de investigar con un xxd la imagen de disco, y después de acomodarla, obtenemos la bandera.
```
Flag: picoCTF{b3_5t111_mL|_<3_ba880921}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)