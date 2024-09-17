## Objetivo
Our flag printing service has started glitching!

Additional details will be available after launching your challenge instance.
## Solución
```
mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ nc saturn.picoctf.net 61048
'picoCTF{gl17ch_m3_n07_' + chr(0x62) + chr(0x64) + chr(0x61) + chr(0x36) + chr(0x38) + chr(0x66) + chr(0x37) + chr(0x35) + '}'
```

- ##### Se hace un pequeño script en Python para descubrir la pieza faltante de la bandera.
``` bash
missingFlag = chr(0x62) + chr(0x64) + chr(0x61) + chr(0x36) + chr(0x38) + chr(0x66) + chr(0x37) + chr(0x35) + '}'
print("picoCTF{gl17ch_m3_n07_" + missingFlag)
```

```
picoCTF{gl17ch_m3_n07_bda68f75}

** Process exited - Return Code: 0 **
Press Enter to exit terminal
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)