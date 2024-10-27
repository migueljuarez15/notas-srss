## Objetivo
The flag is somewhere on this web application not necessarily on the website. Find it.
## Solución
- ##### Al entrar al sitio web, no observamos algo muy fuera de lo común. Accedemos al archivo "robots.txt" para ver si hay información útil, y obtenemos lo siguiente:
```
User-agent *
Disallow: /cgi-bin/
Think you have seen your flag or want to keep looking.

ZmxhZzEudHh0;anMvbXlmaW
anMvbXlmaWxlLnR4dA==
svssshjweuiwl;oiho.bsvdaslejg
Disallow: /wp-admin/
```

- ##### Desencriptamos el texto mediante base64, y obtenemos lo siguiente.
```
flag1.txtjs/myfi
```

- ##### Vamos a acceder a este link, para ver si hay algo interesante.
```
http://saturn.picoctf.net:51543/js/myfile.txt
```

- ##### Al entrar al link, obtenemos la bandera.
```
Flag: picoCTF{Who_D03sN7_L1k5_90B0T5_718c9043}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)