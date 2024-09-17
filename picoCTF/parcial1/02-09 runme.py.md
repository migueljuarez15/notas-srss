## Objetivo
Run the `runme.py` script to get the flag. Download the script with your browser or with `wget` in the webshell.
## Solución
```
mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ wget https://artifacts.picoctf.net/c/34/runme.py
--2024-09-16 22:38:44--  https://artifacts.picoctf.net/c/34/runme.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 18.154.144.104, 18.154.144.85, 18.154.144.103, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|18.154.144.104|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 270 [application/octet-stream]
Saving to: ‘runme.py’

runme.py                      100%[=================================================>]     270  --.-KB/s    in 0s

2024-09-16 22:38:45 (79.1 MB/s) - ‘runme.py’ saved [270/270]

mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ python3 runme.py
picoCTF{run_s4n1ty_run}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)