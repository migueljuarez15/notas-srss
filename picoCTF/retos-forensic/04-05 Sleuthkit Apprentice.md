## Objetivo
Download this disk image and find the flag. Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.
- [Download compressed disk image](https://artifacts.picoctf.net/c/138/disk.flag.img.gz)
## Solución
- ##### Descargamos el archivo, podemos apreciar que es una archivo comprimido ".gz" sobre una imagen de disco ".img", usaremos distintas herramientas para checar la información de la imagen de disco.
```
┌──(kali㉿kali)-[~/picoCTF/SleuthkitApprentice]
└─$ wget https://artifacts.picoctf.net/c/138/disk.flag.img.gz
--2024-10-16 00:19:06--  https://artifacts.picoctf.net/c/138/disk.flag.img.gz
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.26, 3.161.55.100, 3.161.55.64, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.26|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 47534528 (45M) [application/octet-stream]
Saving to: ‘disk.flag.img.gz’

disk.flag.img.gz             100%[============================================>]  45.33M  6.27MB/s    in 7.4s    

2024-10-16 00:19:14 (6.09 MB/s) - ‘disk.flag.img.gz’ saved [47534528/47534528]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/SleuthkitApprentice]
└─$ ls           
disk.flag.img.gz
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/SleuthkitApprentice]
└─$ gzip -d disk.flag.img.gz
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/SleuthkitApprentice]
└─$ file disk.flag.img
disk.flag.img: DOS/MBR boot sector; partition 1 : ID=0x83, active, start-CHS (0x0,32,33), end-CHS (0xc,223,19), startsector 2048, 204800 sectors; partition 2 : ID=0x82, start-CHS (0xc,223,20), end-CHS (0x16,111,25), startsector 206848, 153600 sectors; partition 3 : ID=0x83, start-CHS (0x16,111,26), end-CHS (0x26,62,24), startsector 360448, 253952 sectors
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/SleuthkitApprentice]
└─$ mmls disk.flag.img       
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000206847   0000204800   Linux (0x83)
003:  000:001   0000206848   0000360447   0000153600   Linux Swap / Solaris x86 (0x82)
004:  000:002   0000360448   0000614399   0000253952   Linux (0x83)
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/SleuthkitApprentice]
└─$ fls -o 2048 disk.flag.img
d/d 11: lost+found
r/r 12: ldlinux.sys
r/r 13: ldlinux.c32
r/r 15: config-virt
r/r 16: vmlinuz-virt
r/r 17: initramfs-virt
l/l 18: boot
r/r 20: libutil.c32
r/r 19: extlinux.conf
r/r 21: libcom32.c32
r/r 22: mboot.c32
r/r 23: menu.c32
r/r 14: System.map-virt
r/r 24: vesamenu.c32
V/V 25585:      $OrphanFiles
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/SleuthkitApprentice]
└─$ fls -o 2048 disk.flag.img -r
d/d 11: lost+found
r/r 12: ldlinux.sys
r/r 13: ldlinux.c32
r/r 15: config-virt
r/r 16: vmlinuz-virt
r/r 17: initramfs-virt
l/l 18: boot
r/r 20: libutil.c32
r/r 19: extlinux.conf
r/r 21: libcom32.c32
r/r 22: mboot.c32
r/r 23: menu.c32
r/r 14: System.map-virt
r/r 24: vesamenu.c32
V/V 25585:      $OrphanFiles
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/SleuthkitApprentice]
└─$ fls -o 360448 disk.flag.img -r
d/d 451:        home
d/d 11: lost+found
d/d 12: boot
d/d 1985:       etc
+ r/r 23:       group
.   .   .
++ r/r * 2082(realloc): flag.txt
++ r/r 2371:    flag.uni.txt
d/d 1996:       run
d/d 1997:       srv
d/d 1998:       sys
d/d 2358:       swap
V/V 31745:      $OrphanFiles
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/SleuthkitApprentice]
└─$ fls -o 360448 disk.flag.img -r 3981
r/r * 2082(realloc):    flag.txt
r/r 2371:       flag.uni.txt
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/SleuthkitApprentice]
└─$ fls -o 360448 disk.flag.img -r 1995
r/r 2363:       .ash_history
d/d 3981:       my_folder
+ r/r * 2082(realloc):  flag.txt
+ r/r 2371:     flag.uni.txt
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/SleuthkitApprentice]
└─$ icat -o 360448 disk.flag.img 2363
apk add nano
mkdir my_folder
cd my_folder/
nano flag.txt
ls -al
iconv -f ascii -t utf16 > flag.uni.txt
l
ls -al
iconv -f ascii -t utf16 flag.txt > flag.uni.txt
ls -al
shred
shred -zu flag.txt 
ls -al
halt
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/SleuthkitApprentice]
└─$ icat -o 360448 disk.flag.img 2371
picoCTF{by73_5urf3r_2f22df38}
```

- ##### Usando la instrucción "icat", obtenemos la bandera.
```
Flag: picoCTF{by73_5urf3r_2f22df38}
```
## Notas Adicionales
- **The Sleuth Kit** is a collection of command line tools and a C library that allows you to analyze disk images and recover files from them. It is used behind the scenes in Autopsy and many other open source and commercial forensics tools.
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)