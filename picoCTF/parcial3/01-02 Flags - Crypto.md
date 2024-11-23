## Objetivo
What do the [flags](https://jupiter.challenges.picoctf.org/static/fbeb5f9040d62b18878d199cdda2d253/flag.png) mean?
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Crypto/Flags]
└─$ wget https://jupiter.challenges.picoctf.org/static/fbeb5f9040d62b18878d199cdda2d253/flag.png
--2024-11-23 01:16:51--  https://jupiter.challenges.picoctf.org/static/fbeb5f9040d62b18878d199cdda2d253/flag.png
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 43257 (42K) [application/octet-stream]
Saving to: ‘flag.png’

flag.png                     100%[============================================>]  42.24K  --.-KB/s    in 0.06s   

2024-11-23 01:16:51 (692 KB/s) - ‘flag.png’ saved [43257/43257]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/Flags]
└─$ open flag.png 
```

- ##### Luego de conseguir las letras que representan las banderas en la imagen, obtenemos la bandera.
```
Flag: picoCTF{F1AG5AND5TUFF}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)