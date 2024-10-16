## Objetivo
Use `srch_strings` from the sleuthkit and some terminal-fu to find a flag in this disk image: [dds1-alpine.flag.img.gz](https://mercury.picoctf.net/static/920731987787c93839776ce457d5ecd6/dds1-alpine.flag.img.gz)
## Solución
- ##### Descargamos el archivo, parece ser que tiene multiples extensiones, solo nos centraremos en descomprimir el ".gz" y en buscar strings en ".img".
```
┌──(kali㉿kali)-[~/picoCTF/DiskDiskSleuth]
└─$ sudo apt install sleuthkit              
[sudo] password for kali: 
sleuthkit is already the newest version (4.12.1+dfsg-0kali6).
sleuthkit set to manually installed.
The following packages were automatically installed and are no longer required:
  libavfilter9      libndctl6      libre2-10        openjdk-17-jre           python3-pytzdata
  libdaxctl1        libplacebo338  libroc0.3        openjdk-17-jre-headless  rwho
  libgeos3.12.1t64  libpmem1       libsvtav1enc1d1  python3-diskcache        rwhod
  libjsoncpp25      libpostproc57  libu2f-udev      python3-mistune0         samba-ad-provision
  libjxl0.7         librav1e0      libx265-199      python3-pendulum         samba-dsdb-modules
Use 'sudo apt autoremove' to remove them.

Summary:
  Upgrading: 0, Installing: 0, Removing: 0, Not Upgrading: 0
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/DiskDiskSleuth]
└─$ sudo apt install autopsy  
autopsy is already the newest version (2.24-6kali1).
autopsy set to manually installed.
The following packages were automatically installed and are no longer required:
  libavfilter9      libndctl6      libre2-10        openjdk-17-jre           python3-pytzdata
  libdaxctl1        libplacebo338  libroc0.3        openjdk-17-jre-headless  rwho
  libgeos3.12.1t64  libpmem1       libsvtav1enc1d1  python3-diskcache        rwhod
  libjsoncpp25      libpostproc57  libu2f-udev      python3-mistune0         samba-ad-provision
  libjxl0.7         librav1e0      libx265-199      python3-pendulum         samba-dsdb-modules
Use 'sudo apt autoremove' to remove them.

Summary:
  Upgrading: 0, Installing: 0, Removing: 0, Not Upgrading: 0
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/DiskDiskSleuth]
└─$ wget https://mercury.picoctf.net/static/920731987787c93839776ce457d5ecd6/dds1-alpine.flag.img.gz
--2024-10-15 23:43:06--  https://mercury.picoctf.net/static/920731987787c93839776ce457d5ecd6/dds1-alpine.flag.img.gz
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 29768910 (28M) [application/octet-stream]
Saving to: ‘dds1-alpine.flag.img.gz’

dds1-alpine.flag.img.gz      100%[============================================>]  28.39M  6.26MB/s    in 4.9s    

2024-10-15 23:43:11 (5.84 MB/s) - ‘dds1-alpine.flag.img.gz’ saved [29768910/29768910]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/DiskDiskSleuth]
└─$ file dds1-alpine.flag.img.gz
dds1-alpine.flag.img.gz: gzip compressed data, was "dds1-alpine.flag.img", last modified: Tue Mar 16 00:19:24 2021, from Unix, original size modulo 2^32 134217728
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/DiskDiskSleuth]
└─$ gzip -d dds1-alpine.flag.img.gz
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/DiskDiskSleuth]
└─$ ls
dds1-alpine.flag.img
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/DiskDiskSleuth]
└─$ file dds1-alpine.flag.img    
dds1-alpine.flag.img: DOS/MBR boot sector; partition 1 : ID=0x83, active, start-CHS (0x0,32,33), end-CHS (0x10,81,1), startsector 2048, 260096 sectors
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/DiskDiskSleuth]
└─$ srch_strings dds1-alpine.flag.img | grep picoCTF
  SAY picoCTF{f0r3ns1c4t0r_n30phyt3_564ff1a0}
```

- ##### Una vez buscados los strings con "srch_strings" del Sleuthkit, en el archivo ".img" obtendremos la bandera.
```
Flag: picoCTF{f0r3ns1c4t0r_n30phyt3_564ff1a0}
```
## Notas Adicionales
- **Autopsy** is an easy to use, GUI-based program that allows you to efficiently analyze hard drives and smart phones. It has a plug-in architecture that allows you to find add-on modules or develop custom modules in Java or Python.
- **The Sleuth Kit** is a collection of command line tools and a C library that allows you to analyze disk images and recover files from them. It is used behind the scenes in Autopsy and many other open source and commercial forensics tools.
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)