## Objetivo
The password for the next level is stored in the file **data.txt**, which contains base64 encoded data.
## Datos de Acceso al Nivel
- **Puerto:** 2220
##### Se usará el usuario "bandit10":
- **Usuario:** bandit10
- **Contraseña:** FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
##### Después de conseguir la contraseña en el archivo "data.txt" al decodificarla en base64:
- **Usuario:** bandit11
- **Contraseña descubierta:** dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
## Solución
- ##### Uso de la instrucción "ls -la" para mostrar el contenido del directorio actual.
```
bandit10@bandit:~$ ls -la
total 24
drwxr-xr-x  2 root     root     4096 Jul 17 15:57 .
drwxr-xr-x 70 root     root     4096 Jul 17 15:58 ..
-rw-r--r--  1 root     root      220 Mar 31 08:41 .bash_logout
-rw-r--r--  1 root     root     3771 Mar 31 08:41 .bashrc
-rw-r-----  1 bandit11 bandit10   69 Jul 17 15:57 data.txt
-rw-r--r--  1 root     root      807 Mar 31 08:41 .profile
```

- ##### Uso de la instrucción "cat" para ver el contenido del archivo, al igual que la instrucción "base64 -d" para decodificar el texto.
```
bandit10@bandit:~$ cat data.txt | base64 -d
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```

- ##### Cierre de sesión del usuario "bandit10".
```
bandit10@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.
```
## Notas Adicionales
- **base64** - Es un esquema de codificación de binario a texto, incluye aZaz09+=/
- **ls -la** - Lista archivos de de forma larga y detallada, al igual que todos los archivos (hasta ocultos).
- **cat** - Lista, combina y escribe el contenido de los archivos en la salida estándar.
## Referencias
- [OverTheWire](https://overthewire.org/wargames/bandit/bandit1.html)
- [CyberChef](https://gchq.github.io/CyberChef/)