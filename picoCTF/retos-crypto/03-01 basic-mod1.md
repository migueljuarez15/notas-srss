## Objetivo
We found this weird message being passed around on the servers, we think we have a working decryption scheme. Download the message [here](https://artifacts.picoctf.net/c/129/message.txt). Take each number mod 37 and map it to the following character set: 0-25 is the alphabet (uppercase), 26-35 are the decimal digits, and 36 is an underscore. Wrap your decrypted message in the picoCTF flag format (i.e. `picoCTF{decrypted_message}`)
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Crypto/basic-mod1]
└─$ wget https://artifacts.picoctf.net/c/129/message.txt                                   
--2024-10-23 13:22:05--  https://artifacts.picoctf.net/c/129/message.txt
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.26, 3.161.55.100, 3.161.55.61, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.26|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 86 [application/octet-stream]
Saving to: ‘message.txt’

message.txt                  100%[============================================>]      86  --.-KB/s    in 0s      

2024-10-23 13:22:05 (4.33 MB/s) - ‘message.txt’ saved [86/86]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/basic-mod1]
└─$ cat message.tct
cat: message.tct: No such file or directory
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/basic-mod1]
└─$ cat message.txt
350 63 353 198 114 369 346 184 202 322 94 235 114 110 185 188 225 212 366 374 261 213   
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/basic-mod1]
└─$ nano exp.py    
```

- ##### Creamos el script en Python que decodificara la bandera.
``` python
data = open('message.txt', 'r').read().split()
flag = ''

for c in data:
        char = int(c) % 37
        if char >= 0 and char <= 25:
                s = chr(char + 65)
        elif char >= 26 and char <= 35:
                s = chr(char + 22)
        elif char == 36:
                s = '_'

        flag += s
        print(s)

print(flag)
```

- ##### Ejectuamos el script.
```
┌──(kali㉿kali)-[~/picoCTF/Crypto/basic-mod1]
└─$ python3 exp.py
R
0
U
N
D
_
N
_
R
0
U
N
D
_
A
D
D
1
7
E
C
2
R0UND_N_R0UND_ADD17EC2
```

- ##### Después de ejecutar el script, obtenemos la bandera.
```
Flag: picoCTF{R0UND_N_R0UND_ADD17EC2}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)