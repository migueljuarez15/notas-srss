## Objetivo
This program has constructed the flag using hex ascii values. Identify the flag text by disassembling the program. You can download the file from [here](https://artifacts.picoctf.net/c/508/asciiftw).
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Reversing/ASCII-FTW]
└─$ wget https://artifacts.picoctf.net/c/508/asciiftw                                               
--2024-11-21 02:21:26--  https://artifacts.picoctf.net/c/508/asciiftw
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 13.225.222.120, 13.225.222.125, 13.225.222.105, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|13.225.222.120|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16752 (16K) [application/octet-stream]
Saving to: ‘asciiftw’

asciiftw                     100%[============================================>]  16.36K  --.-KB/s    in 0.001s  

2024-11-21 02:21:26 (11.8 MB/s) - ‘asciiftw’ saved [16752/16752]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/ASCII-FTW]
└─$ chmod +x asciiftw
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/ASCII-FTW]
└─$ ./asciiftw
The flag starts with 70
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/ASCII-FTW]
└─$ gdb -q asciiftw
Reading symbols from asciiftw...
(No debugging symbols found in asciiftw)
(gdb) layout next
```

- ##### Luego de poner el archivo en GDB, nos da esta cadena en hexadecimal, el cual decodificaremos.
```
0x70, 0x69, 0x63, 0x6f, 0x43, 0x54, 0x46, 0x7b, 0x41, 0x53, 0x43, 0x49, 0x49, 0x5f, 0x49, 0x53, 0x5f, 0x45, 0x41, 0x53, 0x59, 0x5f, 0x38, 0x39, 0x36, 0x30, 0x46, 0x30, 0x41, 0x46, 0x7d
```

- ##### Luego de decodificar la cadena, obtenemos la bandera.
```
Flag: picoCTF{ASCII_IS_EASY_8960F0AF}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)