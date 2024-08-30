## Objetivo
The password for the next level is stored in the file **data.txt**, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!).
## Datos de Acceso al Nivel
- **Puerto:** 2220
##### Se usará el usuario "bandit12":
- **Usuario:** bandit12
- **Contraseña:** 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
##### Después de conseguir la contraseña en el archivo "data.txt" al comprimirlo y descomprimirlo varias veces:
- **Usuario:** bandit13
- **Contraseña descubierta:** FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
## Solución
- ##### Se comprime y descomprime varias veces el archivo para poder descubrir la contraseña.
```
bandit12@bandit:~$ xxd -r data.txt | file -
/dev/stdin: gzip compressed data, was "data2.bin", last modified: Wed Jul 17 15:57:06 2024, max compression, from Unix
bandit12@bandit:~$ xxd -r data.txt | zcat |file -
/dev/stdin: bzip2 compressed data, block size = 900k
bandit12@bandit:~$ xxd -r data.txt | zcat | bzcat |file -
/dev/stdin: gzip compressed data, was "data4.bin", last modified: Wed Jul 17 15:57:06 2024, max compression, from Unix
bandit12@bandit:~$ xxd -r data.txt | zcat | bzcat | zcat |file -
/dev/stdin: POSIX tar archive (GNU)
bandit12@bandit:~$ xxd -r data.txt | zcat | bzcat | zcat | tar xO | file -
/dev/stdin: POSIX tar archive (GNU)
bandit12@bandit:~$ xxd -r data.txt | zcat | bzcat | zcat | tar xO | tar xO | file -
/dev/stdin: bzip2 compressed data, block size = 900k
bandit12@bandit:~$ xxd -r data.txt | zcat | bzcat | zcat | tar xO | tar xO | bzcat |file -
/dev/stdin: POSIX tar archive (GNU)
bandit12@bandit:~$ xxd -r data.txt | zcat | bzcat | zcat | tar xO | tar xO | bzcat | tar xO | file -
/dev/stdin: gzip compressed data, was "data9.bin", last modified: Wed Jul 17 15:57:06 2024, max compression, from Unix
bandit12@bandit:~$ xxd -r data.txt | zcat | bzcat | zcat | tar xO | tar xO | bzcat | tar xO | zcat | file -
/dev/stdin: ASCII text
bandit12@bandit:~$ xxd -r data.txt | zcat | bzcat | zcat | tar xO | tar xO | bzcat | tar xO | zcat
The password is FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
```

- ##### Cierre de sesión del usuario "bandit12".
```
bandit12@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.
```
## Notas Adicionales
```
Algunos tipos de compresion en Linux
-----------------------------------------------------
ext comp desc ver en consola
-----------------------------------------------------
.gz gzip gzip -d (gunzip) zcat
.bz2 bzip2 bzip2 -d (bunzip2) bzcat
.tar tar tar xf tar xO
----------------------------------------------------

Otros (instalar) :
.zip zip unzip (7z x)
.rar rar unrar (7z x)
```
## Referencias
- [OverTheWire](https://overthewire.org/wargames/bandit/bandit1.html)
- [Comprimir y Descomprimir archivos en Linux](https://www.ionos.mx/digitalguide/servidores/herramientas/comprimir-y-descomprimir-archivos-usando-tar-para-linux/)