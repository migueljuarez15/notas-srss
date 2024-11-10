## Objetivo
Can you get the flag? Download this [binary](https://artifacts.picoctf.net/c/85/gdbme). Here's the test drive instructions:

- `$ chmod +x gdbme`
- `$ gdb gdbme`
- `(gdb) layout asm`
- `(gdb) break *(main+99)`
- `(gdb) run`
- `(gdb) jump *(main+104)`
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Reversing/GDBTestDrive]
└─$ wget https://artifacts.picoctf.net/c/85/gdbme                                             
--2024-11-06 12:05:05--  https://artifacts.picoctf.net/c/85/gdbme
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.64, 3.161.55.61, 3.161.55.100, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.64|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17048 (17K) [application/octet-stream]
Saving to: ‘gdbme’

gdbme                        100%[============================================>]  16.65K  --.-KB/s    in 0.03s   

2024-11-06 12:05:07 (564 KB/s) - ‘gdbme’ saved [17048/17048]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/GDBTestDrive]
└─$ chmod +x gdbme    
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/GDBTestDrive]
└─$ gdb -q gdbme
Reading symbols from gdbme...
(No debugging symbols found in gdbme)
(gdb) break *(main+99)
Breakpoint 1 at 0x132a
(gdb) run
Starting program: /home/kali/picoCTF/Reversing/GDBTestDrive/gdbme 
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".

Breakpoint 1, 0x000055555555532a in main ()
(gdb) jump *(main+104)
Continuing at 0x55555555532f.
picoCTF{d3bugg3r_dr1v3_197c378a}
[Inferior 1 (process 27042) exited normally]
```

- ##### Luego de ejecutar con el debugger el programa, obtenemos la bandera.
```
Flag: picoCTF{d3bugg3r_dr1v3_197c378a}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)