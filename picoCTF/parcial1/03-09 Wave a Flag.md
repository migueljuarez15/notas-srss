## Objetivo
Can you invoke help flags for a tool or binary? `This program` has extraordinarily helpful information...
## Solución
```
mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ wget https://mercury.picoctf.net/static/fc1d77192c544314efece5dd309092e3/warm
--2024-09-17 00:49:56--  https://mercury.picoctf.net/static/fc1d77192c544314efece5dd309092e3/warm
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10936 (11K) [application/octet-stream]
Saving to: ‘warm.1’

warm                          100%[=================================================>]  10.68K  --.-KB/s    in 0s

2024-09-17 00:49:56 (29.2 MB/s) - ‘warm’ saved [10936/10936]

mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ chmod +x warm
mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ ./warm
Hello user! Pass me a -h to learn what I can do!
mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ ./warm -h
Oh, help? I actually don't do much, but I do have this flag here: picoCTF{b1scu1ts_4nd_gr4vy_6635aa47}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)