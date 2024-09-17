## Objetivo
Can you find the flag in `file` without running it?
## Solución
```
mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ wget https://jupiter.challenges.picoctf.org/static/fae9ac5267cd6e44124e559b901df177/strings
--2024-09-17 00:18:20--  https://jupiter.challenges.picoctf.org/static/fae9ac5267cd6e44124e559b901df177/strings
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 776032 (758K) [application/octet-stream]
Saving to: ‘strings.1’

strings                       100%[=================================================>] 757.84K  2.88MB/s    in 0.3s

2024-09-17 00:18:21 (2.88 MB/s) - ‘strings’ saved [776032/776032]

mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ strings strings
s8561
s4861
s9583
s9176
s9133
s6287
s2587
.   .   .
.gnu.version
.gnu.version_r
.rela.dyn
.rela.plt
.init
.plt.got
.text
.fini
.rodata
.eh_frame_hdr
.eh_frame
.init_array
.fini_array
.dynamic
.data
.bss
.comment

mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ strings strings | grep "picoCTF"
picoCTF{5tRIng5_1T_7f766a23}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)