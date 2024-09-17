## Objetivo
Run the Python script and convert the given number from decimal to binary to get the flag.
## Solución
```
mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ wget https://artifacts.picoctf.net/c/22/convertme.py
--2024-09-16 21:39:13--  https://artifacts.picoctf.net/c/22/convertme.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.225.11, 3.161.225.3, 3.161.225.62, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.225.11|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1189 (1.2K) [application/octet-stream]
Saving to: ‘convertme.py’

convertme.py                  100%[=================================================>]   1.16K  --.-KB/s    in 0s

2024-09-16 21:39:13 (632 MB/s) - ‘convertme.py’ saved [1189/1189]

mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ python3 convertme.py
If 93 is in decimal base, what is it in binary base?
Answer: 1011101
That is correct! Here's your flag: picoCTF{4ll_y0ur_b4535_762f748e}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)