## Objetivo
Download this disk image and find the flag. Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.
- [Download compressed disk image](https://artifacts.picoctf.net/c/213/disk.flag.img.gz)
## Solución
- ##### Descargamos el archivo, podemos apreciar que tenemos una archivo comprimido ".gz", el cual al descomprimirlo obtenemos una imagen de disco ".img", en la cual usaremos diferentes opciones para obtener información de esa imagen.
```
┌──(kali㉿kali)-[~/picoCTF/OperationOrchid]
└─$ wget https://artifacts.picoctf.net/c/213/disk.flag.img.gz
--2024-10-16 00:56:34--  https://artifacts.picoctf.net/c/213/disk.flag.img.gz
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.225.60, 3.161.225.3, 3.161.225.11, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.225.60|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 44360922 (42M) [application/octet-stream]
Saving to: ‘disk.flag.img.gz’

disk.flag.img.gz             100%[============================================>]  42.31M  6.40MB/s    in 6.9s    

2024-10-16 00:56:42 (6.11 MB/s) - ‘disk.flag.img.gz’ saved [44360922/44360922]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/OperationOrchid]
└─$ gzip -d disk.flag.img.gz           
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/OperationOrchid]
└─$ file disk.flag.img
disk.flag.img: DOS/MBR boot sector; partition 1 : ID=0x83, active, start-CHS (0x0,32,33), end-CHS (0xc,223,19), startsector 2048, 204800 sectors; partition 2 : ID=0x82, start-CHS (0xc,223,20), end-CHS (0x19,159,6), startsector 206848, 204800 sectors; partition 3 : ID=0x83, start-CHS (0x19,159,7), end-CHS (0x32,253,11), startsector 411648, 407552 sectors
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/OperationOrchid]
└─$ mmls disk.flag.img   
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000206847   0000204800   Linux (0x83)
003:  000:001   0000206848   0000411647   0000204800   Linux Swap / Solaris x86 (0x82)
004:  000:002   0000411648   0000819199   0000407552   Linux (0x83)
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/OperationOrchid]
└─$ fls -o 0000411648 disk.flag.img    
d/d 460:        home
d/d 11: lost+found
d/d 12: boot
d/d 13: etc
d/d 81: proc
d/d 82: dev
d/d 83: tmp
d/d 84: lib
d/d 87: var
d/d 96: usr
d/d 106:        bin
d/d 120:        sbin
d/d 466:        media
d/d 470:        mnt
d/d 471:        opt
d/d 472:        root
d/d 473:        run
d/d 475:        srv
d/d 476:        sys
d/d 2041:       swap
V/V 51001:      $OrphanFiles
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/OperationOrchid]
└─$ fls -o 0000411648 disk.flag.img 472
r/r 1875:       .ash_history
r/r * 1876(realloc):    flag.txt
r/r 1782:       flag.txt.enc
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/OperationOrchid]
└─$ icat -o 0000411648 disk.flag.img 1782
Salted__�ށ��e��B�J▒�c�$QE&$��4jM�KGeE�1�^Ȥ7� ���؎$�'%                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/OperationOrchid]
└─$ icat -o 0000411648 disk.flag.img 1782 > flag.txt.enc
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/OperationOrchid]
└─$ file flag.txt.enc                  
flag.txt.enc: openssl enc'd data with salted password
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/OperationOrchid]
└─$ icat -o 0000411648 disk.flag.img 1875               
touch flag.txt
nano flag.txt 
apk get nano
apk --help
apk add nano
nano flag.txt 
openssl
openssl aes256 -salt -in flag.txt -out flag.txt.enc -k unbreakablepassword1234567
shred -u flag.txt
ls -al
halt
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/OperationOrchid]
└─$ openssl aes256 -salt -d -in flag.txt.enc -out flag.txt -k unbreakablepassword1234567
*** WARNING : deprecated key derivation used.
Using -iter or -pbkdf2 would be better.
bad decrypt
80C69BC2EE7F0000:error:1C800064:Provider routines:ossl_cipher_unpadblock:bad decrypt:../providers/implementations/ciphers/ciphercommon_block.c:107:
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/OperationOrchid]
└─$ cat flag.txt
picoCTF{h4un71ng_p457_5113beab} 
```

- ##### Una vez desencriptada la contraseña, obtenemos la bandera.
```
Flag: picoCTF{h4un71ng_p457_5113beab}
```
## Notas Adicionales
- **The Sleuth Kit** is a collection of command line tools and a C library that allows you to analyze disk images and recover files from them. It is used behind the scenes in Autopsy and many other open source and commercial forensics tools.
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)