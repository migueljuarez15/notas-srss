## Objetivo
Can you figure out what is in the `eax` register? Put your answer in the picoCTF flag format: `picoCTF{n}` where `n` is the contents of the `eax` register in the decimal number base. If the answer was `0x11` your flag would be `picoCTF{17}`. Download the assembly dump [here](https://artifacts.picoctf.net/c/510/disassembler-dump0_b.txt).
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Reversing/Bit-O-Asm-2]
└─$ wget https://artifacts.picoctf.net/c/510/disassembler-dump0_b.txt
--2024-11-21 04:20:08--  https://artifacts.picoctf.net/c/510/disassembler-dump0_b.txt
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 13.225.222.105, 13.225.222.125, 13.225.222.28, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|13.225.222.105|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 270 [application/octet-stream]
Saving to: ‘disassembler-dump0_b.txt’

disassembler-dump0_b.txt     100%[============================================>]     270  --.-KB/s    in 0s      

2024-11-21 04:20:08 (167 MB/s) - ‘disassembler-dump0_b.txt’ saved [270/270]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/Bit-O-Asm-2]
└─$ cat disassembler-dump0_b.txt
<+0>:     endbr64 
<+4>:     push   rbp
<+5>:     mov    rbp,rsp
<+8>:     mov    DWORD PTR [rbp-0x14],edi
<+11>:    mov    QWORD PTR [rbp-0x20],rsi
<+15>:    mov    DWORD PTR [rbp-0x4],0x9fe1a
<+22>:    mov    eax,DWORD PTR [rbp-0x4]
<+25>:    pop    rbp
<+26>:    ret
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/Bit-O-Asm-2]
└─$ python3
Python 3.11.9 (main, Apr 10 2024, 13:16:36) [GCC 13.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> int("0x9fe1a", 16)
654874
>>> exit()
```

- ##### Después de convertir el número a un entero, obtenemos la bandera.
```
Flag: picoCTF{654874}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)