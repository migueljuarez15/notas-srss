## Objetivo
Can you figure out how this program works to get the flag?
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Reversing/Picker4]
└─$ wget https://artifacts.picoctf.net/c/527/picker-IV
--2024-10-30 13:24:48--  https://artifacts.picoctf.net/c/527/picker-IV
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.26, 3.161.55.64, 3.161.55.61, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.26|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17272 (17K) [application/octet-stream]
Saving to: ‘picker-IV’

picker-IV                    100%[============================================>]  16.87K  --.-KB/s    in 0.002s  

2024-10-30 13:24:49 (9.47 MB/s) - ‘picker-IV’ saved [17272/17272]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/Picker4]
└─$ readelf -a picker-IV | grep win
No processor specific unwind information to decode
    63: 000000000040129e   150 FUNC    GLOBAL DEFAULT   15 win
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/Picker4]
└─$ nc saturn.picoctf.net 61750
Enter the address in hex to jump to, excluding '0x': 40129e
You input 0x40129e
You won!
picoCTF{n3v3r_jump_t0_u53r_5uppl13d_4ddr35535_01672a61}
```

- ##### Luego de analizar el archivo para buscar el código hexadecimal de "win", lo introducimos en el programa y obtenemos la bandera.
```
Flag: picoCTF{n3v3r_jump_t0_u53r_5uppl13d_4ddr35535_01672a61}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)