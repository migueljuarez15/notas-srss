## Objetivo
Can you figure out how this program works to get the flag?
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Reversing/Picker2]
└─$  nc saturn.picoctf.net 57795
==> getRandomNumber
4
==> win
Illegal input
==> print(open('flag.txt', 'r').read())
picoCTF{f1l73r5_f41l_c0d3_r3f4c70r_m1gh7_5ucc33d_0b5f1131}
'NoneType' object is not callable
```

- ##### Luego de realizar la operación que hace la función "win", obtenemos la bandera.
```
Flag: picoCTF{f1l73r5_f41l_c0d3_r3f4c70r_m1gh7_5ucc33d_0b5f1131}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)