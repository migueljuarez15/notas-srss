## Objetivo
This website can be rendered only by **picobrowser**, go and catch the flag! `https://jupiter.challenges.picoctf.org/problem/28921/` ([link](https://jupiter.challenges.picoctf.org/problem/28921/)) or http://jupiter.challenges.picoctf.org:28921
## Solución
- ##### Al querer obtener la bandera, nos dice que nuestro navegador no puede obtenerla si no estamos usando "picobrowser", por lo que, inspeccionaremos la página y nos iremos a las opciones de "Network", esto para cambiar el "User Agent".
```
user-agent:

Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/127.0.0.0 Safari/537.36 OPR/113.0.0.0
```

- ##### Cambiaremos el "User Agent" por "picobrowser", y solicitaremos un nuevo request, lo cual nos proporcionará nuestra bandera.
```
Flag: picoCTF{p1c0_s3cr3t_ag3nt_84f9c865}
```
## Notas Adicionales
- Un user agent es una **aplicación cliente utilizada con un protocolo de red particular**. La expresión se utiliza normalmente como referencia a aquellas que acceden a la World Wide Web. Los User agents de la Web van desde la gama de navegadores, hasta los robots de búsqueda, pasando por los lectores de pantalla.
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)