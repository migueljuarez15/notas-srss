## Objetivo
I stopped using YellowPages and moved onto WhitePages... but [the page they gave me](https://jupiter.challenges.picoctf.org/static/95be9526e162185c741259a75dffa0ab/whitepages.txt) is all blank!
## Solución
- ##### Al descargar el archivo y abrirlo con "cat", vemos que no hay nada realmente, pero al hacerle un "file", vemos que tiene un peso grande.
```
┌──(kali㉿kali)-[~/picoCTF/WhitePages]
└─$ wget https://jupiter.challenges.picoctf.org/static/95be9526e162185c741259a75dffa0ab/whitepages.txt
--2024-10-09 01:24:47--  https://jupiter.challenges.picoctf.org/static/95be9526e162185c741259a75dffa0ab/whitepages.txt
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2976 (2.9K) [application/octet-stream]
Saving to: ‘whitepages.txt’

whitepages.txt               100%[============================================>]   2.91K  --.-KB/s    in 0s      

2024-10-09 01:24:48 (32.8 MB/s) - ‘whitepages.txt’ saved [2976/2976]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/WhitePages]
└─$ cat whitepages.txt                               
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/WhitePages]
└─$ wc whitepages.txt                                                                                 
   0    0 2976 whitepages.txt
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/WhitePages]
└─$ file whitepages.txt
whitepages.txt: Unicode text, UTF-8 text, with very long lines (1376), with no line terminators
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/WhitePages]
└─$ xxd whitepages.txt | head
00000000: e280 83e2 8083 e280 83e2 8083 20e2 8083  ............ ...
00000010: 20e2 8083 e280 83e2 8083 e280 83e2 8083   ...............
00000020: 20e2 8083 e280 8320 e280 83e2 8083 e280   ...... ........
00000030: 83e2 8083 20e2 8083 e280 8320 e280 8320  .... ...... ... 
00000040: 2020 e280 83e2 8083 e280 83e2 8083 e280    ..............
00000050: 8320 20e2 8083 20e2 8083 e280 8320 e280  .  ... ...... ..
00000060: 8320 20e2 8083 e280 83e2 8083 2020 e280  .  .........  ..
00000070: 8320 20e2 8083 2020 2020 e280 8320 e280  .  ...    ... ..
00000080: 83e2 8083 e280 83e2 8083 2020 e280 8320  ..........  ... 
00000090: e280 8320 e280 8320 e280 83e2 8083 e280  ... ... ........
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/WhitePages]
└─$ sudo python3 -m pip install pwntools
[sudo] password for kali: 
DEPRECATION: Loading egg at /usr/local/lib/python3.11/dist-packages/sstv-0.1-py3.11.egg is deprecated. pip 24.3 will enforce this behaviour change. A possible replacement is to use pip for package installation. Discussion can be found at https://github.com/pypa/pip/issues/12330                                           
.   .   .
Successfully built intervaltree
Installing collected packages: unicorn, pyelftools, unix-ar, plumbum, intervaltree, colored-traceback, capstone, rpyc, ropgadget, pwntools
Successfully installed capstone-6.0.0a1 colored-traceback-0.4.2 intervaltree-3.1.0 plumbum-1.9.0 pwntools-4.13.1 pyelftools-0.31 ropgadget-7.5 rpyc-6.0.1 unicorn-2.1.1 unix-ar-0.2.1
WARNING: Running pip as the 'root' user can result in broken permissions and conflicting behaviour with the system package manager, possibly rendering your system unusable.It is recommended to use a virtual environment instead: https://pip.pypa.io/warnings/venv. Use the --root-user-action option if you know what you are doing and want to suppress this warning.                              
```

- ##### Haremos un pequeño script que decodifique los bits del archivo, y al tenerlo completo, obtenemos un texto decodificado.
``` bash
┌──(kali㉿kali)-[~/picoCTF/WhitePages]
└─$ python exp.py                       
bytearray(b'\xe2\x80\x83\xe2\x80\x83\xe2\x80\x83\xe2\x80\x83 \xe2\x80\x83 \xe2\x80\x83\xe2\x80\x83\xe2\x80\x83\xe2\x80\x83\xe2\x80\x83 \xe2\x80\x83\xe2\x80\x83 \xe2\x80\x83\xe2\x80\x83\xe2\x80\x83\xe2\x80\x83 \xe2\x80\x83\xe2\x80\x83 \xe2\x80\x83   
.   .   .
\xe2\x80\x83\xe2\x80\x83\xe2\x80\x83\xe2\x80\x83\xe2\x80\x83  \xe2\x80\x83  \xe2\x80\x83\xe2\x80\x83  \xe2\x80\x83\xe2\x80\x83 \xe2\x80\x83\xe2\x80\x83\xe2\x80\x83  \xe2\x80\x83\xe2\x80\x83\xe2\x80\x83  \xe2\x80\x83     \xe2\x80\x83 \xe2\x80\x83\xe2\x80\x83\xe2\x80\x83\xe2\x80\x83 \xe2\x80\x83 \xe2\x80\x83\xe2\x80\x83\xe2\x80\x83\xe2\x80\x83\xe2\x80\x83 \xe2\x80\x83\xe2\x80\x83 \xe2\x80\x83\xe2\x80\x83\xe2\x80\x83\xe2\x80\x83 \xe2\x80\x83\xe2\x80\x83 ')
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/WhitePages]
└─$ python exp.py
0000 0 00000 00 0000 00 0   00000  0 00 0  000  0  0    0 0000  0 0 0 000 000  00000 0 00000 0 00000 00 0000 00 0 0 00  0 000 0 0 000 0 00 000000 0 00000 0 0 0 0 0000 00 00  000 00 00 0 0000  00 000000 0 00 00 000 0 0 0000  0 00    0 0 00 00 000 000 0 00  00 0000000 00  000 000000 0000 00 00000 0 0000  0 00 0  0 000   0 0 00 00 00    0 0 0 0 0 00   00 000 0000 000000 0 00 00 000 0 0 0 00000 00    0 0 00 00 0 0 000000 0 00000 00 0000 00 00  0 0 00  000000  000000  000000 000000 000  00  0    0   00 00  000 00  00 0 0   00  00 000000 00000 0   0  00  00 0 00 0  0000 000000 0 00000  0 00 0   0 000   0 000   00  0  000 00   0 0 0   00 00  00   0  0 00000 0  0000 000000 0 00000 00000 00 0000000  000 00  0 0 00  00 000  000 00  00  0000 0 00000 00 0000 00 0   00000  0 00 0  000  0  0    0 0000  0 0 0 000 000  00    0  0  0   00  0    0   0 000 0     0  0000 0  0  000  0  000 0     0   00  0   00000  0000 0  000  0  00 0 0   00  0 0     0  0000 0   00 00  00 0 0 0     0  000  0   00 00  00 0 0  0000 0   0 000  00 0 0  00 000 0     0  00 0 0   000 0   0 0 0  0000 0  0  000 0     00  0   00  000 00  000000  000000   00000  0  000  00000  000 000  00000  00  00  0000 00  0   00  0   00   00 0  0000 00  0 0 0  000 00  00 0000   0000  000  0  00 0 00  00 000   00 0  00  000  00 000  0 000  00  000  0 0 00   00000  0  00  00 000  000  0     0 0000 0 00000 00 0000 00 
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/WhitePages]
└─$ python exp.py
bytearray(b'00001010000010010000100101110000011010010110001101101111010000110101010001000110000010100000101000001001000010010101001101000101010001010010000001010000010101010100001001001100010010010100001100100000010100100100010101000011010011110101001001000100010100110010000000100110001000000100001001000001010000110100101101000111010100100100111101010101010011100100010000100000010100100100010101010000010011110101001001010100000010100000100100001001001101010011000000110000001100000010000001000110011011110111001001100010011001010111001100100000010000010111011001100101001011000010000001010000011010010111010001110100011100110110001001110101011100100110011101101000001011000010000001010000010000010010000000110001001101010011001000110001001100110000101000001001000010010111000001101001011000110110111101000011010101000100011001111011011011100110111101110100010111110110000101101100011011000101111101110011011100000110000101100011011001010111001101011111011000010111001001100101010111110110001101110010011001010110000101110100011001010110010001011111011001010111000101110101011000010110110001011111001101110011000100110000001100000011100000110110001100000110001000110000011001100110000100110111001101110011100101100001001101010110001001100100001110000110001101100101001100100011100101100110001100100011010001100110001101010011100000110110011001000110001101111101000010100000100100001001')
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/WhitePages]
└─$ nano exp.py  
                                                                                                                  

from pwn import *

file = open('whitepages.txt', 'rb')
data = bytearray(file.read())
data = data.replace(b'\xe2\x80\x83', b'0')
data = data.replace(b'\x20', b'1')
data = data.decode('ascii')
data = unbits(data)

print(data)

┌──(kali㉿kali)-[~/picoCTF/WhitePages]
└─$ python exp.py
b'\n\t\tpicoCTF\n\n\t\tSEE PUBLIC RECORDS & BACKGROUND REPORT\n\t\t5000 Forbes Ave, Pittsburgh, PA 15213\n\t\tpicoCTF{not_all_spaces_are_created_equal_7100860b0fa779a5bd8ce29f24f586dc}\n\t\t'
```

- ##### Finalmente, obtenemos la bandera.
```
Flag: picoCTF{not_all_spaces_are_created_equal_7100860b0fa779a5bd8ce29f24f586dc}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)