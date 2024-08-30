## Objetivo
The password for the next level can be retrieved by submitting the password of the current level to **port 30000 on localhost**.
## Datos de Acceso al Nivel
- **Puerto:** 2220
##### Se usará el usuario "bandit14":
- **Usuario:** bandit14
- **Contraseña:** MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
##### Después de conseguir la contraseña en el localhost con puerto 30000:
- **Usuario:** bandit15
- **Contraseña descubierta:** 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
## Solución
- ##### Uso de la instrucción "nc localhost 30000" para conectarse a un host remoto.
```
bandit14@bandit:~$ ls
bandit14@bandit:~$ ls -la
total 24
drwxr-xr-x  3 root root 4096 Jul 17 15:57 .
drwxr-xr-x 70 root root 4096 Jul 17 15:58 ..
-rw-r--r--  1 root root  220 Mar 31 08:41 .bash_logout
-rw-r--r--  1 root root 3771 Mar 31 08:41 .bashrc
-rw-r--r--  1 root root  807 Mar 31 08:41 .profile
drwxr-xr-x  2 root root 4096 Jul 17 15:57 .ssh
bandit14@bandit:~$ nc localhost 30000
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
Correct!
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
```

- ##### Cierre de sesión del usuario "bandit14".
```
bandit14@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.
```
## Notas Adicionales
- **nc** - Es una herramienta que permite conectarse a un host remoto, tambien podemos abrir un puerto nc localhost 3000 localhost - es el host o la maquina a la que me quiero conectar.
## Referencias
- [OverTheWire](https://overthewire.org/wargames/bandit/bandit1.html)