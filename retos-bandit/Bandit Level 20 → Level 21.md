## Objetivo
There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

**NOTE:** Try connecting to your own network daemon to see if it works as you think
## Datos de Acceso al Nivel
- **Puerto:** 2220
##### Se usará el usuario "bandit20":
- **Usuario:** bandit20
- **Contraseña:** 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
##### Después de conseguir la contraseña:
- **Usuario:** bandit21
- **Contraseña descubierta:** EeoULMCra2q0dSkYj561DX7s1CpBuOBt
## Solución
```
bandit20@bandit:~$ ls
suconnect
bandit20@bandit:~$ ls -la
total 36
drwxr-xr-x  2 root     root      4096 Jul 17 15:57 .
drwxr-xr-x 70 root     root      4096 Jul 17 15:58 ..
-rw-r--r--  1 root     root       220 Mar 31 08:41 .bash_logout
-rw-r--r--  1 root     root      3771 Mar 31 08:41 .bashrc
-rw-r--r--  1 root     root       807 Mar 31 08:41 .profile
-rwsr-x---  1 bandit21 bandit20 15604 Jul 17 15:57 suconnect
bandit20@bandit:~$ ./suconnect 3030
Could not connect
bandit20@bandit:~$ nc -lnvp 5050
Listening on 0.0.0.0 5050
^C
bandit20@bandit:~$ nc localhost 5050
bandit20@bandit:~$ nc localhost 5050
hola quien eres
^C
bandit20@bandit:~$ nc -lnvp 1618 <<<0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO &
[1] 3139816
bandit20@bandit:~$ Listening on 0.0.0.0 1618
^C
bandit20@bandit:~$ ls -la
total 36
drwxr-xr-x  2 root     root      4096 Jul 17 15:57 .
drwxr-xr-x 70 root     root      4096 Jul 17 15:58 ..
-rw-r--r--  1 root     root       220 Mar 31 08:41 .bash_logout
-rw-r--r--  1 root     root      3771 Mar 31 08:41 .bashrc
-rw-r--r--  1 root     root       807 Mar 31 08:41 .profile
-rwsr-x---  1 bandit21 bandit20 15604 Jul 17 15:57 suconnect
bandit20@bandit:~$ ./suconnect
Usage: ./suconnect <portnumber>
This program will connect to the given port on localhost using TCP. If it receives the correct password from the other side, the next password is transmitted back.
bandit20@bandit:~$ ./suconnect  1618
Connection received on 127.0.0.1 40244
Read: 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
Password matches, sending next password
EeoULMCra2q0dSkYj561DX7s1CpBuOBt
[1]+  Done                    nc -lnvp 1618 <<< 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
```

- ##### Cierre de sesión del usuario "bandit20".
```
bandit20@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.
```
## Notas Adicionales
- **&** - Si agregamos este símbolo al final de un comando lo estamos enviando al segundo plano (background).
- **Jobs** - Me muestra que comandos estan en el segundo plano.
## Referencias
- [OverTheWire](https://overthewire.org/wargames/bandit/bandit1.html)