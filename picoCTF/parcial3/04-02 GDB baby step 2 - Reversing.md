## Objetivo
Can you figure out what is in the `eax` register at the end of the `main` function? Put your answer in the picoCTF flag format: `picoCTF{n}` where `n` is the contents of the `eax` register in the decimal number base. If the answer was `0x11` your flag would be `picoCTF{17}`. Debug [this](https://artifacts.picoctf.net/c/520/debugger0_b).
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Reversing/GDB-Baby-Step-2]
└─$ wget https://artifacts.picoctf.net/c/520/debugger0_b                        
--2024-11-21 22:18:17--  https://artifacts.picoctf.net/c/520/debugger0_b
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 13.225.222.28, 13.225.222.125, 13.225.222.105, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|13.225.222.28|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16304 (16K) [application/octet-stream]
Saving to: ‘debugger0_b’

debugger0_b                  100%[============================================>]  15.92K  --.-KB/s    in 0s      

2024-11-21 22:18:18 (259 MB/s) - ‘debugger0_b’ saved [16304/16304]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/GDB-Baby-Step-2]
└─$ file debugger0_b
debugger0_b: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=95b0203be2982e75dbc01d1cc25b1309f7aec5f7, for GNU/Linux 3.2.0, not stripped
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/GDB-Baby-Step-2]
└─$ chmod +x debugger0_b
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/GDB-Baby-Step-2]
└─$ gdb -q debugger0_b  
Reading symbols from debugger0_b...
(No debugging symbols found in debugger0_b)
(gdb) disassemble main
Dump of assembler code for function main:
   0x0000000000401106 <+0>:     endbr64
   0x000000000040110a <+4>:     push   %rbp
   0x000000000040110b <+5>:     mov    %rsp,%rbp
   0x000000000040110e <+8>:     mov    %edi,-0x14(%rbp)
   0x0000000000401111 <+11>:    mov    %rsi,-0x20(%rbp)
   0x0000000000401115 <+15>:    movl   $0x1e0da,-0x4(%rbp)
   0x000000000040111c <+22>:    movl   $0x25f,-0xc(%rbp)
   0x0000000000401123 <+29>:    movl   $0x0,-0x8(%rbp)
   0x000000000040112a <+36>:    jmp    0x401136 <main+48>
   0x000000000040112c <+38>:    mov    -0x8(%rbp),%eax
   0x000000000040112f <+41>:    add    %eax,-0x4(%rbp)
   0x0000000000401132 <+44>:    addl   $0x1,-0x8(%rbp)
   0x0000000000401136 <+48>:    mov    -0x8(%rbp),%eax
   0x0000000000401139 <+51>:    cmp    -0xc(%rbp),%eax
   0x000000000040113c <+54>:    jl     0x40112c <main+38>
   0x000000000040113e <+56>:    mov    -0x4(%rbp),%eax
   0x0000000000401141 <+59>:    pop    %rbp
   0x0000000000401142 <+60>:    ret
End of assembler dump.
(gdb) break main
Breakpoint 1 at 0x40110e
(gdb) run
Starting program: /home/kali/picoCTF/Reversing/GDB-Baby-Step-2/debugger0_b 
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".

Breakpoint 1, 0x000000000040110e in main ()
(gdb) break *0x401142
Breakpoint 2 at 0x401142
(gdb) continue
Continuing.

Breakpoint 2, 0x0000000000401142 in main ()
(gdb) info registers rip
rip            0x401142            0x401142 <main+60>
(gdb) print/d $eax
$1 = 307019
(gdb) exit
A debugging session is active.

        Inferior 1 [process 58851] will be killed.

Quit anyway? (y or n) y
```

- ##### Después de convertir el número a un entero, obtenemos la bandera.
```
Flag: picoCTF{307019}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)