## Objetivo
After all this `git` stuff, it’s time for another escape. Good luck!
## Datos de Acceso al Nivel
- **Puerto:** 2220
##### Se usará el usuario "bandit32":
- **Usuario:** bandit32
- **Contraseña:** 3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K
##### Después de conseguir la contraseña:
- **Usuario:** bandit33
- **Contraseña descubierta:** tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0
## Solución
```
WELCOME TO THE UPPERCASE SHELL
>> ls
sh: 1: LS: Permission denied
>> $0
$ ls -la
total 36
drwxr-xr-x  2 root     root      4096 Jul 17 15:57 .
drwxr-xr-x 70 root     root      4096 Jul 17 15:58 ..
-rw-r--r--  1 root     root       220 Mar 31 08:41 .bash_logout
-rw-r--r--  1 root     root      3771 Mar 31 08:41 .bashrc
-rw-r--r--  1 root     root       807 Mar 31 08:41 .profile
-rwsr-x---  1 bandit33 bandit32 15136 Jul 17 15:57 uppershell
$ cat /etc/bandit_pass/bandit33
tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0
```

- ##### Cierre de sesión del usuario "bandit32".
```
$ exit
>> ^C
Connection to bandit.labs.overthewire.org closed.
```
## Notas Adicionales
## Referencias
- [OverTheWire](https://overthewire.org/wargames/bandit/bandit1.html)