## Objetivo
A musician left us a [message](https://jupiter.challenges.picoctf.org/static/d5570d48262dbba2a31f2a940409ad9d/message.txt). What's it mean?
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Crypto/Mr-Worlwide]
└─$ wget https://jupiter.challenges.picoctf.org/static/d5570d48262dbba2a31f2a940409ad9d/message.txt
--2024-11-23 01:32:09--  https://jupiter.challenges.picoctf.org/static/d5570d48262dbba2a31f2a940409ad9d/message.txt
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 278 [application/octet-stream]
Saving to: ‘message.txt’

message.txt                  100%[============================================>]     278  --.-KB/s    in 0s      

2024-11-23 01:32:10 (9.17 MB/s) - ‘message.txt’ saved [278/278]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/Mr-Worlwide]
└─$ cat message.txt                
picoCTF{(35.028309, 135.753082)(46.469391, 30.740883)(39.758949, -84.191605)(41.015137, 28.979530)(24.466667, 54.366669)(3.140853, 101.693207)_(9.005401, 38.763611)(-3.989038, -79.203560)(52.377956, 4.897070)(41.085651, -73.858467)(57.790001, -152.407227)(31.205753, 29.924526)}
```

- ##### Buscaremos las coordenadas en Google Maps.
```
Coordenadas:
Kyoto, Japan				
Odessa, Ukraine				
Dayton, United States			
Istanbul, Turkey			
Abu Dhabi, United Arab Emirates		
Kuala Lumpur, Malaysia			
_					
Addis Ababa, Ethiophia			
Loja, Ecuador				
Amsterdam, Netherlands			
Sleepy Hollow, United States		
Kodiak, United States			
Alexandria, Egypt
```

- ##### Luego de tener las primeras letras de cada lugar, obtenemos la bandera.
```
Flag: picoCTF{KODIAK_ALASKA}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)