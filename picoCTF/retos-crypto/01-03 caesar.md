## Objetivo
Decrypt this [message](https://jupiter.challenges.picoctf.org/static/7d707a443e95054dc4cf30b1d9522ef0/ciphertext).
## Solución
- ##### Descargamos el archivo, y podemos apreciar que es un texto, que analizándolo, está encriptado mediante un algoritmo de rotación, por lo que mediante el uso de CyberChef, trataremos de buscar cuantas veces se rotó.
```
┌──(kali㉿kali)-[~/picoCTF/Crypto/caesar]
└─$ wget https://jupiter.challenges.picoctf.org/static/7d707a443e95054dc4cf30b1d9522ef0/ciphertext
--2024-10-16 12:59:58--  https://jupiter.challenges.picoctf.org/static/7d707a443e95054dc4cf30b1d9522ef0/ciphertext
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 35 [application/octet-stream]
Saving to: ‘ciphertext’

ciphertext                   100%[============================================>]      35  --.-KB/s    in 0s      

2024-10-16 13:00:13 (36.9 MB/s) - ‘ciphertext’ saved [35/35]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/caesar]
└─$ cat ciphertext
picoCTF{gvswwmrkxlivyfmgsrhnrisegl}
```

- ##### Una vez rotada 22 veces la cadena, obtenemos la parte encriptada de la bandera.
```
Flag: picoCTF{crossingtherubicondjneoach}
```
## Notas Adicionales
- En criptografía, el **cifrado César**, también conocido como cifrado por desplazamiento, código de César o desplazamiento de César, es una de las técnicas de cifrado más simples y más usadas. Es un tipo de cifrado por sustitución en el que una letra en el texto original es reemplazada por otra letra que se encuentra un número fijo de posiciones más adelante en el alfabeto. 
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)
- [CyberChef](https://gchq.github.io/CyberChef/)