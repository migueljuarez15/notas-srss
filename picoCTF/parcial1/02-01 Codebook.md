## Objetivo
Run the Python script `code.py` in the same directory as `codebook.txt`.
## Solución
```
mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ wget https://artifacts.picoctf.net/c/3/code.py
--2024-09-16 21:37:08--  https://artifacts.picoctf.net/c/3/code.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.225.60, 3.161.225.3, 3.161.225.11, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.225.60|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1278 (1.2K) [application/octet-stream]
Saving to: ‘code.py’

code.py                       100%[=================================================>]   1.25K  --.-KB/s    in 0s

2024-09-16 21:37:09 (383 MB/s) - ‘code.py’ saved [1278/1278]

mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ wget https://artifacts.picoctf.net/c/3/codebook.txt
--2024-09-16 21:37:18--  https://artifacts.picoctf.net/c/3/codebook.txt
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.225.60, 3.161.225.3, 3.161.225.11, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.225.60|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 27 [application/octet-stream]
Saving to: ‘codebook.txt’

codebook.txt                  100%[=================================================>]      27  --.-KB/s    in 0s

2024-09-16 21:37:19 (13.3 MB/s) - ‘codebook.txt’ saved [27/27]

mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ python3 code.py
picoCTF{c0d3b00k_455157_197a982c}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)