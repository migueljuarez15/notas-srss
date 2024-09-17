## Objetivo
Sometimes you need to handle process data outside of a file. Can you find a way to keep the output from this program and search for the flag? Connect to `jupiter.challenges.picoctf.org 4427`.
## Solución
```
mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ nc jupiter.challenges.picoctf.org 4427 > flag.txt
^C
mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ cat flag.txt | grep "picoCTF"
picoCTF{digital_plumb3r_5ea1fbd7}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)