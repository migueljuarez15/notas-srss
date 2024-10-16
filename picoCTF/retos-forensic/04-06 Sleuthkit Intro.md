## Objetivo
Download the disk image and use `mmls` on it to find the size of the Linux partition. Connect to the remote checker service to check your answer and get the flag. Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory. [Download disk image](https://artifacts.picoctf.net/c/164/disk.img.gz)

## Solución
- ##### Descargamos el archivo, se aprecia que viene comprimido en ".gz", y es una imagen de disco ".img", la abriremos con el "mmls" para ver la información que contiene.
```
┌──(kali㉿kali)-[~/picoCTF/SleuthkitIntro]
└─$ wget https://artifacts.picoctf.net/c/164/disk.img.gz                                            
--2024-10-15 23:56:19--  https://artifacts.picoctf.net/c/164/disk.img.gz
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.225.3, 3.161.225.62, 3.161.225.11, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.225.3|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 29714372 (28M) [application/octet-stream]
Saving to: ‘disk.img.gz’

disk.img.gz                  100%[============================================>]  28.34M  6.18MB/s    in 4.7s    

2024-10-15 23:56:24 (6.04 MB/s) - ‘disk.img.gz’ saved [29714372/29714372]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/SleuthkitIntro]
└─$ gzip disk.img.gz               
gzip: disk.img.gz already has .gz suffix -- unchanged
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/SleuthkitIntro]
└─$ gzip -d disk.img.gz
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/SleuthkitIntro]
└─$ ls
disk.img
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/SleuthkitIntro]
└─$ file disk.img            
disk.img: DOS/MBR boot sector; partition 1 : ID=0x83, active, start-CHS (0x0,32,33), end-CHS (0xc,190,50), startsector 2048, 202752 sectors
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/SleuthkitIntro]
└─$ mmls disk.img       
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000204799   0000202752   Linux (0x83)
```

- ##### Una vez lanzando la instancia, nos pregunta el tamaño de la partición Linux en el archivo descargado.
```
┌──(kali㉿kali)-[~/picoCTF/SleuthkitIntro]
└─$ nc saturn.picoctf.net 60231 
What is the size of the Linux partition in the given disk image?
Length in sectors: 0000202752
0000202752
Great work!
picoCTF{mm15_f7w!}
```

- ##### Una vez contestado correctamente, obtenemos la bandera.
```
Flag: picoCTF{mm15_f7w!}
```
## Notas Adicionales
- **The Sleuth Kit** is a collection of command line tools and a C library that allows you to analyze disk images and recover files from them. It is used behind the scenes in Autopsy and many other open source and commercial forensics tools.
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)