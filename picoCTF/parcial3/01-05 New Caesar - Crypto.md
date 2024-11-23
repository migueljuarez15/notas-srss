## Objetivo
We found a brand new type of encryption, can you break the secret code? (Wrap with picoCTF{}) `apbopjbobpnjpjnmnnnmnlnbamnpnononpnaaaamnlnkapndnkncamnpapncnbannaapncndnlnpna` [new_caesar.py](https://mercury.picoctf.net/static/d8a6722e08659449dd091668c0c9bbca/new_caesar.py)
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Crypto/NewCaesar]
└─$ wget https://mercury.picoctf.net/static/d8a6722e08659449dd091668c0c9bbca/new_caesar.py         
--2024-11-23 01:39:20--  https://mercury.picoctf.net/static/d8a6722e08659449dd091668c0c9bbca/new_caesar.py
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 589 [application/octet-stream]
Saving to: ‘new_caesar.py’

new_caesar.py                100%[============================================>]     589  --.-KB/s    in 0s      

2024-11-23 01:39:20 (24.7 MB/s) - ‘new_caesar.py’ saved [589/589]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/NewCaesar]
└─$ cat new_caesar.py
import string

LOWERCASE_OFFSET = ord("a")
ALPHABET = string.ascii_lowercase[:16]

def b16_encode(plain):
        enc = ""
        for c in plain:
                binary = "{0:08b}".format(ord(c))
                enc += ALPHABET[int(binary[:4], 2)]
                enc += ALPHABET[int(binary[4:], 2)]
        return enc

def shift(c, k):
        t1 = ord(c) - LOWERCASE_OFFSET
        t2 = ord(k) - LOWERCASE_OFFSET
        return ALPHABET[(t1 + t2) % len(ALPHABET)]

flag = "redacted"
key = "redacted"
assert all([k in ALPHABET for k in key])
assert len(key) == 1

b16 = b16_encode(flag)
enc = ""
for i, c in enumerate(b16):
        enc += shift(c, key[i % len(key)])
print(enc)
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/NewCaesar]
└─$ nano solve.py  
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/NewCaesar]
└─$ python3 solve.py     
ùÙùÜÝÜÛÑ
        ßÞÞßÐ
             ÛÚÓÚÒ
ÐÒÓÛßÐ            ßÒÑ
ÈèËÌËÊÀûÎÍÍÎÏÿûÊÉþÂÉÁûÎþÁÀüÏþÁÂÊÎÏ
íü×üý·×º»º¹¿ê½¼¼½¾îê¹¸í±¸°ê½í°¿ë¾í°±¹½¾
ÜëÆëì¦Æ©ª©¨®Ù¬««¬­ÝÙ¨§Ü §¯Ù¬Ü¯®Ú­Ü¯ ¨¬­
ËÚµÚÛµÈÌÈËÈÉË
ºÉ¤ÉÊ¤·»·º·º¸º
©¸¸¹svwvu{¦yxxyzª¦ut©}t|¦y©|{§z©|}uyz
§§¨befedjhgghidclckhkjikldhi
qQqTUTSYWVVWXSR[RZWZYXZ[SWX
v`@`CDCBHsFEEFGwsBAvJAIsFvIHtGvIJBFG
et_tu?_23217b54456fb10e908b5e87c6e89156
TcNcd.N!"! &Q$##$%UQ /T(/'Q$T'&R%T'( $%
CR=RS=@D@C@CAC
2A,AB
?202 ,?3?
!01ûÿþýó.ñððñò".ýü!õüô.ñ!ôó/ò!ôõýñò
/
/ ê
íîíìâàïïàáìëäëãàãâáãäìàá
```

- ##### Después de crear el script y decodificar el texto, obtenemos la bandera.
```
Flag: picoCTF{et_tu?_23217b54456fb10e908b5e87c6e89156}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)