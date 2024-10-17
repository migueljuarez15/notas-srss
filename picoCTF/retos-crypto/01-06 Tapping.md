## Objetivo
Theres tapping coming in from the wires. What's it saying `nc jupiter.challenges.picoctf.org 48247`.
## Solución
- ##### Al conectarnos al netcat, podemos ver que nos dan un texto completamente encriptado, usaremos el algoritmo de Morse para desencriptarlo.
```
┌──(kali㉿kali)-[~/picoCTF/Crypto/Tapping]
└─$ nc jupiter.challenges.picoctf.org 48247
.--. .. -.-. --- -.-. - ..-. { -- ----- .-. ... ...-- -.-. ----- -.. ...-- .---- ... ..-. ..- -. .---- ..--- -.... .---- ....- ...-- ---.. .---- ---.. .---- } 
```

- ##### Una vez desencriptado el código Morse, obtenemos la bandera.
```
Flag: PICOCTF{M0RS3C0D31SFUN1261438181}
```
## Notas Adicionales
- El **código morse,** también conocido como **alfabeto morse** o **clave morse** es un sistema de representación de letras y números mediante señales emitidas de forma intermitente.
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)
- [CyberChef](https://gchq.github.io/CyberChef/)