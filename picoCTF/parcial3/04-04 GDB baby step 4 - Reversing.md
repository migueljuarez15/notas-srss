## Objetivo
`main` calls a function that multiplies `eax` by a constant. The flag for this challenge is that constant in decimal base. If the constant you find is 0x1000, the flag will be `picoCTF{4096}`. Debug [this](https://artifacts.picoctf.net/c/532/debugger0_d).
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Reversing/GDB-Baby-Step-4]
└─$ wget https://artifacts.picoctf.net/c/532/debugger0_d
--2024-11-21 23:33:50--  https://artifacts.picoctf.net/c/532/debugger0_d
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 13.225.222.28, 13.225.222.120, 13.225.222.125, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|13.225.222.28|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16328 (16K) [application/octet-stream]
Saving to: ‘debugger0_d’

debugger0_d                  100%[============================================>]  15.95K  --.-KB/s    in 0.003s  

2024-11-21 23:33:50 (5.06 MB/s) - ‘debugger0_d’ saved [16328/16328]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/GDB-Baby-Step-4]
└─$ gdb -q debugger0_d
Reading symbols from debugger0_d...
(No debugging symbols found in debugger0_d)
(gdb) disassemble main
Dump of assembler code for function main:
   0x000000000040111c <+0>:     endbr64
   0x0000000000401120 <+4>:     push   %rbp
   0x0000000000401121 <+5>:     mov    %rsp,%rbp
   0x0000000000401124 <+8>:     sub    $0x20,%rsp
   0x0000000000401128 <+12>:    mov    %edi,-0x14(%rbp)
   0x000000000040112b <+15>:    mov    %rsi,-0x20(%rbp)
   0x000000000040112f <+19>:    movl   $0x28e,-0x4(%rbp)
   0x0000000000401136 <+26>:    movl   $0x0,-0x8(%rbp)
   0x000000000040113d <+33>:    mov    -0x4(%rbp),%eax
   0x0000000000401140 <+36>:    mov    %eax,%edi
   0x0000000000401142 <+38>:    call   0x401106 <func1>
   0x0000000000401147 <+43>:    mov    %eax,-0x8(%rbp)
   0x000000000040114a <+46>:    mov    -0x4(%rbp),%eax
   0x000000000040114d <+49>:    leave
   0x000000000040114e <+50>:    ret
End of assembler dump.
(gdb) disassemble func1
Dump of assembler code for function func1:
   0x0000000000401106 <+0>:     endbr64
   0x000000000040110a <+4>:     push   %rbp
   0x000000000040110b <+5>:     mov    %rsp,%rbp
   0x000000000040110e <+8>:     mov    %edi,-0x4(%rbp)
   0x0000000000401111 <+11>:    mov    -0x4(%rbp),%eax
   0x0000000000401114 <+14>:    imul   $0x3269,%eax,%eax
   0x000000000040111a <+20>:    pop    %rbp
   0x000000000040111b <+21>:    ret
End of assembler dump.
(gdb) exit
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/GDB-Baby-Step-4]
└─$ python3         
Python 3.11.9 (main, Apr 10 2024, 13:16:36) [GCC 13.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> int("0x3269", 16)
12905
>>> exit()
```

- ##### Después de convertir el número a un entero, obtenemos la bandera.
```
Flag: picoCTF{12905}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)