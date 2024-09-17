## Objetivo
Can you look at the data in this binary: `static`? This `BASH script` might help!
## Solución
```
mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ wget https://mercury.picoctf.net/static/e9dd71b5d11023873b8abe99cdb45551/static
--2024-09-17 00:10:14--  https://mercury.picoctf.net/static/e9dd71b5d11023873b8abe99cdb45551/static
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8376 (8.2K) [application/octet-stream]
Saving to: ‘static’

static                        100%[=================================================>]   8.18K  --.-KB/s    in 0s

2024-09-17 00:10:14 (24.0 MB/s) - ‘static’ saved [8376/8376]

mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ wget https://mercury.picoctf.net/static/e9dd71b5d11023873b8abe99cdb45551/ltdis.sh
--2024-09-17 00:10:23--  https://mercury.picoctf.net/static/e9dd71b5d11023873b8abe99cdb45551/ltdis.sh
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 785 [application/octet-stream]
Saving to: ‘ltdis.sh’

ltdis.sh                      100%[=================================================>]     785  --.-KB/s    in 0s

2024-09-17 00:10:23 (434 MB/s) - ‘ltdis.sh’ saved [785/785]

mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ file static
static: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=7eb9ee1907cc878f15f9949988893b1f0ab1ebdf, not stripped
mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ file ltdis.sh
ltdis.sh: Bourne-Again shell script, ASCII text executable

mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ cat ltdis.sh
#!/bin/bash

echo "Attempting disassembly of $1 ..."


#This usage of "objdump" disassembles all (-D) of the first file given by
#invoker, but only prints out the ".text" section (-j .text) (only section
#that matters in almost any compiled program...

objdump -Dj .text $1 > $1.ltdis.x86_64.txt


#Check that $1.ltdis.x86_64.txt is non-empty
#Continue if it is, otherwise print error and eject

if [ -s "$1.ltdis.x86_64.txt" ]
then
        echo "Disassembly successful! Available at: $1.ltdis.x86_64.txt"

        echo "Ripping strings from binary with file offsets..."
        strings -a -t x $1 > $1.ltdis.strings.txt
        echo "Any strings found in $1 have been written to $1.ltdis.strings.txt with file offset"

else
        echo "Disassembly failed!"
        echo "Usage: ltdis.sh <program-file>"
        echo "Bye!"
fi

mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ ./ltdis.sh static
Attempting disassembly of static ...
Disassembly successful! Available at: static.ltdis.x86_64.txt
Ripping strings from binary with file offsets...
Any strings found in static have been written to static.ltdis.strings.txt with file offset
mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ cat static.ltdis.strings.txt | grep "picoCTF"
   1020 picoCTF{d15a5m_t34s3r_ae0b3ef2}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)