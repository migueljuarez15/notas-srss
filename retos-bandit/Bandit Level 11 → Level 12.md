## Objetivo
The password for the next level is stored in the file **data.txt**, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions.
## Datos de Acceso al Nivel
- **Puerto:** 2220
##### Se usará el usuario "bandit11":
- **Usuario:** bandit11
- **Contraseña:** dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
##### Después de conseguir la contraseña en el archivo "data.txt" al decodificarla en modo rot13:
- **Usuario:** bandit12
- **Contraseña descubierta:** 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
## Solución
- ##### Uso de la instrucción "cat" para ver el contenido del archivo, al igual que la instrucción "tr {a-zA-Z} {n-Za-mN-ZA-M}" para decodificar el texto en formato rot13.
```
bandit11@bandit:~$ cat data.txt | tr [a-zA-Z] [n-za-mN-ZA-M]
The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```

- ##### Cierre de sesión del usuario "bandit11".
```
bandit11@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.
```
## Notas Adicionales
- **rot13** - A simple caesar substitution cipher which **rot**ates alphabet characters by the specified amount (default 13).
- **cat** - Lista, combina y escribe el contenido de los archivos en la salida estándar.
- **tr** - Permite el reemplazo o eliminación de un conjunto de caracteres de la Entrada estándar.
## Referencias
- [OverTheWire](https://overthewire.org/wargames/bandit/bandit1.html)
- [CyberChef](https://gchq.github.io/CyberChef/)
- [tr (Unix)](https://es.wikipedia.org/wiki/Tr_(Unix))