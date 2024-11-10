## Objetivo
We have recovered a [binary](https://jupiter.challenges.picoctf.org/static/31c9b832d036a10daeef52d8b4290ef0/rev) and a [text file](https://jupiter.challenges.picoctf.org/static/31c9b832d036a10daeef52d8b4290ef0/rev_this). Can you reverse the flag.
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Reversing/reverse-cipher]
└─$ wget https://jupiter.challenges.picoctf.org/static/31c9b832d036a10daeef52d8b4290ef0/rev           
--2024-11-06 12:17:56--  https://jupiter.challenges.picoctf.org/static/31c9b832d036a10daeef52d8b4290ef0/rev
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16856 (16K) [application/octet-stream]
Saving to: ‘rev’

rev                          100%[============================================>]  16.46K  --.-KB/s    in 0s      

2024-11-06 12:17:57 (210 MB/s) - ‘rev’ saved [16856/16856]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/reverse-cipher]
└─$ wget https://jupiter.challenges.picoctf.org/static/31c9b832d036a10daeef52d8b4290ef0/rev_this
--2024-11-06 12:18:08--  https://jupiter.challenges.picoctf.org/static/31c9b832d036a10daeef52d8b4290ef0/rev_this
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 24 [application/octet-stream]
Saving to: ‘rev_this’

rev_this                     100%[============================================>]      24  --.-KB/s    in 0s      

2024-11-06 12:18:10 (45.1 MB/s) - ‘rev_this’ saved [24/24]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/reverse-cipher]
└─$ file rev                 
rev: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=523d51973c11197605c76f84d4afb0fe9e59338c, not stripped
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/reverse-cipher]
└─$ file rev_this
rev_this: ASCII text, with no line terminators
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/reverse-cipher]
└─$ chmod +x rev  
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/reverse-cipher]
└─$ ./rev
No flag found, please make sure this is run on the server
zsh: segmentation fault  ./rev
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/reverse-cipher]
└─$ cat rev_this      
picoCTF{w1{1wq85jc=2i0<}                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/reverse-cipher]
└─$ gdb -q rev    
Reading symbols from rev...
(No debugging symbols found in rev)
(gdb) info functions
All defined functions:

Non-debugging symbols:
0x0000000000001000  _init
0x0000000000001030  puts@plt
0x0000000000001040  fread@plt
0x0000000000001050  fclose@plt
0x0000000000001060  fputc@plt
0x0000000000001070  fopen@plt
0x0000000000001080  exit@plt
0x0000000000001090  __cxa_finalize@plt
0x00000000000010a0  _start
0x00000000000010d0  deregister_tm_clones
0x0000000000001100  register_tm_clones
0x0000000000001140  __do_global_dtors_aux
0x0000000000001180  frame_dummy
0x0000000000001185  main
0x00000000000012d0  __libc_csu_init
0x0000000000001330  __libc_csu_fini
0x0000000000001334  _fini
(gdb) exit
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/reverse-cipher]
└─$ nano solve.py          
                                                                                                                           
┌──(kali㉿kali)-[~/picoCTF/Reversing/reverse-cipher]
└─$ cat solve.py

rev = open('rev_this').read()
flag = ''

for i in range(8):
        flag += rev[i]

for j in range(8, 24):
        if (j & 1 == 0):
                flag += chr(ord(rev[j]) - 5)
        else:
                flag += chr(ord(rev[j]) + 2)

flag += rev[23]
print(flag)
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/reverse-cipher]
└─$ python3 solve.py
picoCTF{r3v3rs37ee84d27}
```

- ##### Una vez reverseado el código fuente con Ghidra, y realizando el script en Python, obtenemos la bandera.
```
Flag: picoCTF{r3v3rs37ee84d27}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)