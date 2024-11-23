## Objetivo
Can you get the flag? Reverse engineer this [Python program](https://artifacts.picoctf.net/c/48/unpackme.flag.py).
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Reversing/unpackme.py]
└─$ wget https://artifacts.picoctf.net/c/48/unpackme.flag.py                                  
--2024-11-22 01:02:03--  https://artifacts.picoctf.net/c/48/unpackme.flag.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.61, 3.161.55.26, 3.161.55.100, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.61|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 527 [application/octet-stream]
Saving to: ‘unpackme.flag.py’

unpackme.flag.py             100%[============================================>]     527  --.-KB/s    in 0s      

2024-11-22 01:02:05 (16.5 MB/s) - ‘unpackme.flag.py’ saved [527/527]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/unpackme.py]
└─$ cat unpackme.flag.py 
import base64
from cryptography.fernet import Fernet



payload = b'gAAAAABkzWGO_8MlYpNM0n0o718LL-w9m3rzXvCMRFghMRl6CSZwRD5DJOvN_jc8TFHmHmfiI8HWSu49MyoYKvb5mOGm_Jn4kkhC5fuRiGgmwEpxjh0z72dpi6TaPO2TorksAd2bNLemfTaYPf9qiTn_z9mvCQYV9cFKK9m1SqCSr4qDwHXgkQpm7IJAmtEJqyVUfteFLszyxv5-KXJin5BWf9aDPIskp4AztjsBH1_q9e5FIwIq48H7AaHmR8bdvjcW_ZrvhAIOInm1oM-8DjamKvhh7u3-lA=='

key_str = 'correctstaplecorrectstaplecorrec'
key_base64 = base64.b64encode(key_str.encode())
f = Fernet(key_base64)
plain = f.decrypt(payload)
exec(plain.decode())
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/unpackme.py]
└─$ nano unpackme.flag.py
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/unpackme.py]
└─$ cat unpackme.flag.py
import base64
from cryptography.fernet import Fernet



payload = b'gAAAAABkzWGO_8MlYpNM0n0o718LL-w9m3rzXvCMRFghMRl6CSZwRD5DJOvN_jc8TFHmHmfiI8HWSu49MyoYKvb5mOGm_Jn4kkhC5fuRiGgmwEpxjh0z72dpi6TaPO2TorksAd2bNLemfTaYPf9qiTn_z9mvCQYV9cFKK9m1SqCSr4qDwHXgkQpm7IJAmtEJqyVUfteFLszyxv5-KXJin5BWf9aDPIskp4AztjsBH1_q9e5FIwIq48H7AaHmR8bdvjcW_ZrvhAIOInm1oM-8DjamKvhh7u3-lA=='

key_str = 'correctstaplecorrectstaplecorrec'
key_base64 = base64.b64encode(key_str.encode())
f = Fernet(key_base64)
plain = f.decrypt(payload)
print(plain.decode())
##exec(plain.decode())
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/unpackme.py]
└─$ python3 unpackme.flag.py

pw = input('What\'s the password? ')

if pw == 'batteryhorse':
  print('picoCTF{175_chr157m45_5274ff21}')
else:
  print('That password is incorrect.')
```

- ##### Luego de modificar el archivo de Python, obtenemos la bandera.
```
Flag: picoCTF{175_chr157m45_5274ff21}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)