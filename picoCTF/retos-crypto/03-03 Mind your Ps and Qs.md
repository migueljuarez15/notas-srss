## Objetivo
In RSA, a small `e` value can be problematic, but what about `N`? Can you decrypt this? [values](https://mercury.picoctf.net/static/12d820e355a7775a2c9129b2622a7eb6/values)
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Crypto/MindYourPsAndQs]
└─$ wget https://mercury.picoctf.net/static/12d820e355a7775a2c9129b2622a7eb6/values                         
--2024-10-23 12:25:03--  https://mercury.picoctf.net/static/12d820e355a7775a2c9129b2622a7eb6/values
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 206 [application/octet-stream]
Saving to: ‘values’

values                       100%[============================================>]     206  --.-KB/s    in 0s      

2024-10-23 12:25:10 (248 MB/s) - ‘values’ saved [206/206]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/MindYourPsAndQs]
└─$ cat values    
Decrypt my super sick RSA:
c: 843044897663847841476319711639772861390329326681532977209935413827620909782846667
n: 1422450808944701344261903748621562998784243662042303391362692043823716783771691667
e: 65537                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/MindYourPsAndQs]
└─$ python3                                                                        
Python 3.11.9 (main, Apr 10 2024, 13:16:36) [GCC 13.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> c = 843044897663847841476319711639772861390329326681532977209935413827620909782846667
>>> e = 65537
>>> p = 2159947535959146091116171018558446546179
>>> q = 658558036833541874645521278345168572231473
>>> n = p * q
>>> n
1422450808944701344261903748621562998784243662042303391362692043823716783771691667
>>> tn = (p - 1) * (q - 1)
>>> tn
1422450808944701344261903748621562998783582944057933890341955406374353056752914016
>>> d = pow(e, -1, tn)
>>> d
975120122884150896343356420256053234758228648361853546720066993334766006694511009
>>> m = pow(c, d, n)
>>> m
13016382529449106065927291425342535437996222135352905256639555294957886055592061
>>> bytes.fromhex(hex(m)[2:]).decode()
'picoCTF{sma11_N_n0_g0od_00264570}'
>>> exit()
```

- ##### Después de decodificarlo con el script en Python, obtenemos la bandera.
```
Flag: picoCTF{sma11_N_n0_g0od_00264570}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)