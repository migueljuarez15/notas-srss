## Objetivo
Can you figure out what is in the `eax` register at the end of the `main` function? Put your answer in the picoCTF flag format: `picoCTF{n}` where `n` is the contents of the `eax` register in the decimal number base. If the answer was `0x11` your flag would be `picoCTF{17}`. Disassemble [this](https://artifacts.picoctf.net/c/512/debugger0_a).
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Reversing/GDB-Baby-Step-1]
└─$ wget https://artifacts.picoctf.net/c/512/debugger0_a                               
--2024-11-21 21:04:59--  https://artifacts.picoctf.net/c/512/debugger0_a
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 13.225.222.120, 13.225.222.105, 13.225.222.125, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|13.225.222.120|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16472 (16K) [application/octet-stream]
Saving to: ‘debugger0_a’

debugger0_a                  100%[============================================>]  16.09K  --.-KB/s    in 0s      

2024-11-21 21:05:00 (196 MB/s) - ‘debugger0_a’ saved [16472/16472]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/GDB-Baby-Step-1]
└─$ file debugger0_a         
debugger0_a: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=15a10290db2cd2ec0c123cf80b88ed7d7f5cf9ff, for GNU/Linux 3.2.0, not stripped
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/GDB-Baby-Step-1]
└─$ gdb -q debugger0_a
Reading symbols from debugger0_a...
(No debugging symbols found in debugger0_a)
(gdb) disassemble main
Dump of assembler code for function main:
   0x0000000000001129 <+0>:     endbr64
   0x000000000000112d <+4>:     push   %rbp
   0x000000000000112e <+5>:     mov    %rsp,%rbp
   0x0000000000001131 <+8>:     mov    %edi,-0x4(%rbp)
   0x0000000000001134 <+11>:    mov    %rsi,-0x10(%rbp)
   0x0000000000001138 <+15>:    mov    $0x86342,%eax
   0x000000000000113d <+20>:    pop    %rbp
   0x000000000000113e <+21>:    ret
End of assembler dump.
(gdb) exit
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/GDB-Baby-Step-1]
└─$ python3           
Python 3.11.9 (main, Apr 10 2024, 13:16:36) [GCC 13.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> int("0x86342", 16)
549698
>>> exit()
```

- ##### Después de convertir el número a un entero, obtenemos la bandera.
```
Flag: picoCTF{549698}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)