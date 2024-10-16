## Objetivo
Download this disk image, find the key and log into the remote machine. Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.
## Solución
- ##### Descargamos el archivo, y podemos apreciar que es un archivo comprimido ".gz" el cual al descomprimirlo nos genera una imagen de disco ".img", en la que buscaremos información importante (la key_file) para poder conectarnos a la instancia.
```
┌──(kali㉿kali)-[~/picoCTF/OperationOni]
└─$ wget https://artifacts.picoctf.net/c/71/disk.img.gz      
--2024-10-16 01:12:46--  https://artifacts.picoctf.net/c/71/disk.img.gz
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.225.11, 3.161.225.62, 3.161.225.3, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.225.11|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 48132743 (46M) [application/octet-stream]
Saving to: ‘disk.img.gz’

disk.img.gz                  100%[============================================>]  45.90M  6.26MB/s    in 9.6s    

2024-10-16 01:12:56 (4.76 MB/s) - ‘disk.img.gz’ saved [48132743/48132743]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/OperationOni]
└─$ gzip -d disk.img.gz     
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/OperationOni]
└─$ mmls disk.img     
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000206847   0000204800   Linux (0x83)
003:  000:001   0000206848   0000471039   0000264192   Linux (0x83)
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/OperationOni]
└─$ fls -o 0000206848 disk.img -r      
d/d 458:        home
d/d 11: lost+found
d/d 12: boot
d/d 13: etc
+ r/r 24:       group-
+ r/r 25:       shadow
.   .   .
d/d 470:        root
+ r/r 2344:     .ash_history
+ d/d 3916:     .ssh
++ r/r 2345:    id_ed25519
++ r/r 2346:    id_ed25519.pub
d/d 471:        run
d/d 473:        srv
d/d 474:        sys
V/V 33049:      $OrphanFiles
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/OperationOni]
└─$ fls -o 0000206848 disk.img 470 -r
r/r 2344:       .ash_history
d/d 3916:       .ssh
+ r/r 2345:     id_ed25519
+ r/r 2346:     id_ed25519.pub
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/OperationOni]
└─$ icat -o 0000206848 disk.img 2344     
ssh-keygen -t ed25519
ls .ssh/
halt
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/OperationOni]
└─$ icat -o 0000206848 disk.img 2345
-----BEGIN OPENSSH PRIVATE KEY-----
b3BlbnNzaC1rZXktdjEAAAAABG5vbmUAAAAEbm9uZQAAAAAAAAABAAAAMwAAAAtzc2gtZW
QyNTUxOQAAACBgrXe4bKNhOzkCLWOmk4zDMimW9RVZngX51Y8h3BmKLAAAAJgxpYKDMaWC
gwAAAAtzc2gtZWQyNTUxOQAAACBgrXe4bKNhOzkCLWOmk4zDMimW9RVZngX51Y8h3BmKLA
AAAECItu0F8DIjWxTp+KeMDvX1lQwYtUvP2SfSVOfMOChxYGCtd7hso2E7OQItY6aTjMMy
KZb1FVmeBfnVjyHcGYosAAAADnJvb3RAbG9jYWxob3N0AQIDBAUGBw==
-----END OPENSSH PRIVATE KEY-----
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/OperationOni]
└─$ icat -o 0000206848 disk.img 2345 > key_file
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/OperationOni]
└─$ chmod 600 key_file
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/OperationOni]
└─$ ssh -i key_file -p 56542 ctf-player@saturn.picoctf.net
The authenticity of host '[saturn.picoctf.net]:56542 ([13.59.203.175]:56542)' can't be established.
ED25519 key fingerprint is SHA256:XBSvB1lk28EctsAVdKJtsl0A7C5bonqPrvHCYH8aEy4.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[saturn.picoctf.net]:56542' (ED25519) to the list of known hosts.
Welcome to Ubuntu 20.04.5 LTS (GNU/Linux 6.5.0-1023-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

ctf-player@challenge:~$ ls
flag.txt
ctf-player@challenge:~$ cat flag.txt
picoCTF{k3y_5l3u7h_af277f77}
ctf-player@challenge:~$ 
Connection to saturn.picoctf.net closed by remote host.
Connection to saturn.picoctf.net closed.
```

- ##### Una vez conectados en la instancia, usaremos "ls" para listar los archivos y un "cat" para obtener la bandera del archivo "flag.txt".
```
Flag: picoCTF{k3y_5l3u7h_af277f77}
```
## Notas Adicionales
- **The Sleuth Kit** is a collection of command line tools and a C library that allows you to analyze disk images and recover files from them. It is used behind the scenes in Autopsy and many other open source and commercial forensics tools.
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)