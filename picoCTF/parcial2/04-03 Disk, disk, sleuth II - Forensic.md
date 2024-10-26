## Objetivo
All we know is the file with the flag is named `down-at-the-bottom.txt`... Disk image: [dds2-alpine.flag.img.gz](https://mercury.picoctf.net/static/626abf12c976b994999f77eec3138a22/dds2-alpine.flag.img.gz)
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Forensics/DiskDiskSleuthII]
└─$ wget https://mercury.picoctf.net/static/626abf12c976b994999f77eec3138a22/dds2-alpine.flag.img.gz
--2024-10-26 04:46:26--  https://mercury.picoctf.net/static/626abf12c976b994999f77eec3138a22/dds2-alpine.flag.img.gz
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 29770589 (28M) [application/octet-stream]
Saving to: ‘dds2-alpine.flag.img.gz’

dds2-alpine.flag.img.gz      100%[============================================>]  28.39M  5.50MB/s    in 5.6s    

2024-10-26 04:46:32 (5.09 MB/s) - ‘dds2-alpine.flag.img.gz’ saved [29770589/29770589]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/DiskDiskSleuthII]
└─$ gzip -d dds2-alpine.flag.img.gz
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/DiskDiskSleuthII]
└─$ ls
dds2-alpine.flag.img
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/DiskDiskSleuthII]
└─$ file dds2-alpine.flag.img
dds2-alpine.flag.img: DOS/MBR boot sector; partition 1 : ID=0x83, active, start-CHS (0x0,32,33), end-CHS (0x10,81,1), startsector 2048, 260096 sectors
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/DiskDiskSleuthII]
└─$ mmls dds2-alpine.flag.img
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000262143   0000260096   Linux (0x83)
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/DiskDiskSleuthII]
└─$ fsstat dds2-alpine.flag.img -o 2048
FILE SYSTEM INFORMATION
--------------------------------------------
File System Type: Ext3
Volume Name: 
Volume ID: dc53a3bb0ae739a5164c89db56bbb12f
.   .   .
Group: 15:
  Inode Range: 30481 - 32512
  Block Range: 122881 - 130047
  Layout:
    Data bitmap: 122881 - 122881
    Inode bitmap: 122882 - 122882
    Inode Table: 122883 - 123136
    Data Blocks: 122883 - 122882, 123137 - 130047
  Free Inodes: 2032 (100%)
  Free Blocks: 1920 (26%)
  Total Directories: 0
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/DiskDiskSleuthII]
└─$ fsstat dds2-alpine.flag.img -o 2048 | head
FILE SYSTEM INFORMATION
--------------------------------------------
File System Type: Ext3
Volume Name: 
Volume ID: dc53a3bb0ae739a5164c89db56bbb12f

Last Written at: 2021-02-16 13:21:20 (EST)
Last Checked at: 2021-02-16 13:21:19 (EST)

Last Mounted at: 2021-02-16 13:21:19 (EST)
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/DiskDiskSleuthII]
└─$ fls -r dds2-alpine.flag.img -o 2048 | grep down
++ d/d 2177:    if-down.d
++ d/d 2178:    if-post-down.d
++ d/d 2180:    if-pre-down.d
++ d/d 2204:    shutdown
+ r/r 18291:    down-at-the-bottom.txt
+ l/l 18311:    ifdown
+ r/r 18344:    openrc-shutdown
+++++ r/r 12472:        down.sh
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/DiskDiskSleuthII]
└─$ icat ./dds2-alpine.flag.img -o 2048 18291
   _     _     _     _     _     _     _     _     _     _     _     _     _  
  / \   / \   / \   / \   / \   / \   / \   / \   / \   / \   / \   / \   / \ 
 ( p ) ( i ) ( c ) ( o ) ( C ) ( T ) ( F ) ( { ) ( f ) ( 0 ) ( r ) ( 3 ) ( n )
  \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/ 
   _     _     _     _     _     _     _     _     _     _     _     _     _  
  / \   / \   / \   / \   / \   / \   / \   / \   / \   / \   / \   / \   / \ 
 ( s ) ( 1 ) ( c ) ( 4 ) ( t ) ( 0 ) ( r ) ( _ ) ( n ) ( 0 ) ( v ) ( 1 ) ( c )
  \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/ 
   _     _     _     _     _     _     _     _     _     _     _  
  / \   / \   / \   / \   / \   / \   / \   / \   / \   / \   / \ 
 ( 3 ) ( _ ) ( 0 ) ( d ) ( 9 ) ( d ) ( 9 ) ( e ) ( c ) ( b ) ( } )
  \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/ 
                                                                  
```

- ##### Una vez encontrando el texto, obtenemos la bandera.
```
Flag: picoCTF{f0r3ns1c4t0r_n0v1c3_0d9d9ecb}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)