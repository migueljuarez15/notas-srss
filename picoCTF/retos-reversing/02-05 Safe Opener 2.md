## Objetivo
What can you do with this file? I forgot the key to my safe but this [file](https://artifacts.picoctf.net/c/291/SafeOpener.class) is supposed to help me with retrieving the lost key. Can you help me unlock my safe?
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Reversing/SafeOpener2]
└─$ wget https://artifacts.picoctf.net/c/291/SafeOpener.class                                          
--2024-10-30 12:21:20--  https://artifacts.picoctf.net/c/291/SafeOpener.class
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.100, 3.161.55.61, 3.161.55.26, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.100|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2036 (2.0K) [application/octet-stream]
Saving to: ‘SafeOpener.class’

SafeOpener.class             100%[============================================>]   1.99K  --.-KB/s    in 0s      

2024-10-30 12:21:21 (58.9 MB/s) - ‘SafeOpener.class’ saved [2036/2036]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/SafeOpener2]
└─$ file SafeOpener.clas                           
SafeOpener.clas: cannot open `SafeOpener.clas' (No such file or directory)
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/SafeOpener2]
└─$ file SafeOpener.class
SafeOpener.class: compiled Java class data, version 52.0 (Java 1.8)
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/SafeOpener2]
└─$ strings SafeOpener.class | grep picoCTF                 
,picoCTF{SAf3_0p3n3rr_y0u_solv3d_it_198203f7}
```

- ##### Después de aplicar un strings al archivo ".class" de un archivo compilado, obtenemos la bandera.
```
Flag: picoCTF{SAf3_0p3n3rr_y0u_solv3d_it_198203f7}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)