## Objetivo
This is the Custom Cyclical Cipher! Download the ciphertext [here](https://artifacts.picoctf.net/c_titan/47/ciphertext). Download the encoder [here](https://artifacts.picoctf.net/c_titan/47/convert.py). Enclose the flag in our wrapper for submission. If the flag was "example" you would submit "picoCTF{example}".
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Crypto/C3]
└─$ wget https://artifacts.picoctf.net/c_titan/47/ciphertext
--2024-11-23 00:59:45--  https://artifacts.picoctf.net/c_titan/47/ciphertext
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 13.225.222.28, 13.225.222.120, 13.225.222.105, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|13.225.222.28|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 237 [application/octet-stream]
Saving to: ‘ciphertext’

ciphertext                   100%[============================================>]     237  --.-KB/s    in 0s      

2024-11-23 00:59:46 (441 MB/s) - ‘ciphertext’ saved [237/237]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/C3]
└─$ wget https://artifacts.picoctf.net/c_titan/47/convert.py
--2024-11-23 00:59:59--  https://artifacts.picoctf.net/c_titan/47/convert.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 13.225.222.125, 13.225.222.105, 13.225.222.120, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|13.225.222.125|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 335 [application/octet-stream]
Saving to: ‘convert.py’

convert.py                   100%[============================================>]     335  --.-KB/s    in 0s      

2024-11-23 00:59:59 (243 MB/s) - ‘convert.py’ saved [335/335]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/C3]
└─$ cat ciphertext
DLSeGAGDgBNJDQJDCFSFnRBIDjgHoDFCFtHDgJpiHtGDmMAQFnRBJKkBAsTMrsPSDDnEFCFtIbEDtDCIbFCFtHTJDKerFldbFObFCFtLBFkBAAAPFnRBJGEkerFlcPgKkImHnIlATJDKbTbFOkdNnsgbnJRMFnRBNAFkBAAAbrcbTKAkOgFpOgFpOpkBAAAAAAAiClFGIPFnRBaKliCgClFGtIBAAAAAAAOgGEkImHnIl                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/C3]
└─$ cat convert.py
import sys
chars = ""
from fileinput import input
for line in input():
  chars += line

lookup1 = "\n \"#()*+/1:=[]abcdefghijklmnopqrstuvwxyz"
lookup2 = "ABCDEFGHIJKLMNOPQRSTabcdefghijklmnopqrst"

out = ""

prev = 0
for char in chars:
  cur = lookup1.index(char)
  out += lookup2[(cur - prev) % 40]
  prev = cur

sys.stdout.write(out)

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/C3]
└─$ nano convert.py                    
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/C3]
└─$ cat ciphertext | python3 convert.py
#asciiorder
#fortychars
#selfinput
#pythontwo

chars = ""
from fileinput import input
for line in input():
    chars += line
b = 1 / 1

for i in range(len(chars)):
    if i == b * b * b:
        print chars[i] #prints
        b += 1 / 1

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/C3]
└─$ cat ciphertext | python3 convert.py > solve.py
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/C3]
└─$ cat solve.py | python2 solve.py               
a
d
l
i
b
s
```

- ##### Después de decodificar el texto cifrado y ver que era un archivo de Python2, al ejecutarlo obtenemos la bandera.
```
Flag: picoCTF{adlibs}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)