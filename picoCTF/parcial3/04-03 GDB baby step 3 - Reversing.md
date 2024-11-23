## Objetivo
Now for something a little different. `0x2262c96b` is loaded into memory in the `main` function. Examine byte-wise the memory that the constant is loaded in by using the GDB command `x/4xb addr`. The flag is the four bytes as they are stored in memory. If you find the bytes `0x11 0x22 0x33 0x44` in the memory location, your flag would be: `picoCTF{0x11223344}`. Debug [this](https://artifacts.picoctf.net/c/531/debugger0_c).
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Reversing/GDB-Baby-Step-3]
└─$ wget https://artifacts.picoctf.net/c/531/debugger0_c
--2024-11-21 23:16:42--  https://artifacts.picoctf.net/c/531/debugger0_c
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.100, 3.161.55.61, 3.161.55.64, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.100|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16304 (16K) [application/octet-stream]
Saving to: ‘debugger0_c’

debugger0_c                  100%[============================================>]  15.92K  --.-KB/s    in 0.02s   

2024-11-21 23:16:44 (664 KB/s) - ‘debugger0_c’ saved [16304/16304]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/GDB-Baby-Step-3]
└─$ chmod +x debugger0_c
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/GDB-Baby-Step-3]
└─$ gdb -q debugger0_c  
Reading symbols from debugger0_c...
(No debugging symbols found in debugger0_c)
(gdb) disassemble main
Dump of assembler code for function main:
   0x0000000000401106 <+0>:     endbr64
   0x000000000040110a <+4>:     push   %rbp
   0x000000000040110b <+5>:     mov    %rsp,%rbp
   0x000000000040110e <+8>:     mov    %edi,-0x14(%rbp)
   0x0000000000401111 <+11>:    mov    %rsi,-0x20(%rbp)
   0x0000000000401115 <+15>:    movl   $0x2262c96b,-0x4(%rbp)
   0x000000000040111c <+22>:    mov    -0x4(%rbp),%eax
   0x000000000040111f <+25>:    pop    %rbp
   0x0000000000401120 <+26>:    ret
End of assembler dump.
(gdb) break main
Breakpoint 1 at 0x40110e
(gdb) r
Starting program: /home/kali/picoCTF/Reversing/GDB-Baby-Step-3/debugger0_c 
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".

Breakpoint 1, 0x000000000040110e in main ()
(gdb) break *0x40111f
Breakpoint 2 at 0x40111f
(gdb) continue
Continuing.

Breakpoint 2, 0x000000000040111f in main ()
(gdb) x/4xb $rbp-0x4
0x7fffffffdd0c: 0x6b    0xc9    0x62    0x22
(gdb) exit
A debugging session is active.

        Inferior 1 [process 66851] will be killed.

Quit anyway? (y or n) y
```

- ##### Después de convertir el número a un entero, obtenemos la bandera.
```
Flag: picoCTF{0x6bc96222}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)