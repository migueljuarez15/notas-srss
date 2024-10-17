## Objetivo
The [numbers](https://jupiter.challenges.picoctf.org/static/f209a32253affb6f547a585649ba4fda/the_numbers.png)... what do they mean?
## Solución
- ##### Descargamos el archivo, podemos apreciar que es una imagen ".png" que contiene una cadena de texto encriptada, usaremos CyberChef para decodificarla.
```
┌──(kali㉿kali)-[~/picoCTF/Crypto/TheNumbers]
└─$ wget https://jupiter.challenges.picoctf.org/static/f209a32253affb6f547a585649ba4fda/the_numbers.png
--2024-10-17 14:24:42--  https://jupiter.challenges.picoctf.org/static/f209a32253affb6f547a585649ba4fda/the_numbers.png
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 100721 (98K) [application/octet-stream]
Saving to: ‘the_numbers.png’

the_numbers.png              100%[============================================>]  98.36K  67.3KB/s    in 1.5s    

2024-10-17 14:24:54 (67.3 KB/s) - ‘the_numbers.png’ saved [100721/100721]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/TheNumbers]
└─$ open the_numbers.png
```

- ##### Abriendo la imagen, nos dan la cadena a desencriptarla. Lo haremos con el algoritmo A1Z26.
```
CADENA DE TEXTO ENCRIPTADA:
16 9 3 15 3 20 6 { 20 8 5 14 21 13 2 5 18 19 13 1 19 15 14 }
```

- ##### Una vez descifrada la cadena, obtenemos la bandera.
```
Flag: picoctf{thenumbersmason}
```
## Notas Adicionales
- **A1Z26** es un cifrado por sustitución directa muy simple, donde cada letra del alfabeto se reemplaza por su número en el alfabeto.
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)
- [CyberChef](https://gchq.github.io/CyberChef/)