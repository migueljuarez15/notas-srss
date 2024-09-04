## Objetivo
There are 2 files in the homedirectory: **passwords.old and passwords.new**. The password for the next level is in **passwords.new** and is the only line that has been changed between **passwords.old and passwords.new**

**NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19**
## Datos de Acceso al Nivel
- **Puerto:** 2220
##### Se usará el usuario "bandit17":
- **Usuario:** bandit17
- **Contraseña:** EReVavePLFHtFlFsjn3hyzMlvSuSAcRD
##### Después de conseguir la contraseña:
- **Usuario:** bandit18
- **Contraseña descubierta:** x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
## Solución
```
bandit17@bandit:~$ cat /etc/bandit_pass/bandit17
EReVavePLFHtFlFsjn3hyzMlvSuSAcRD
bandit17@bandit:~$ ls
passwords.new  passwords.old
bandit17@bandit:~$ wc -l passwords.
passwords.new  passwords.old
bandit17@bandit:~$ wc -l passwords.
passwords.new  passwords.old
bandit17@bandit:~$ wc -l passwords.
passwords.new  passwords.old
bandit17@bandit:~$ diff passwords.old passwords.new
42c42
< bSrACvJvvBSxEM2SGsV5sn09vc3xgqyp
---
> x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
```

- ##### Cierre de sesión del usuario "bandit17".
```
bandit17@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.
```
## Notas Adicionales
- **cat** - Lista, combina y escribe el contenido de los archivos en la salida estándar.
- **wc -l** - Cuenta el numero de líneas que tiene un archivo de texto.
- **diff** - Comparación entre dos directorios.
## Referencias
- [OverTheWire](https://overthewire.org/wargames/bandit/bandit1.html)