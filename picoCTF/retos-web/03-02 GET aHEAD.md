## Objetivo
Find the flag being held on this server to get ahead of the competition [http://mercury.picoctf.net:28916/](http://mercury.picoctf.net:28916/)
## Solución
- ##### Al entrar a la página web e inspeccionar el código, en el apartado de Network, el request "GET" lo cambiaremos por un request "HEAD".
```
GET v | http://mercury.picoctf.net:28916/

HEAD v | http://mercury.picoctf.net:28916/
```

- ##### Al volver a mandar el request, obtenemos la bandera.
```
|---|---|
|HEAD||
|scheme|http|
|host|mercury.picoctf.net:28916|
|filename|/|
||   |
|Address|18.189.209.142:28916|

Status

200

OK

VersionHTTP/1.1

Transferred103 B (0 B size)

|---|---|
|Content-type|text/html; charset=UTF-8|

|---|---|
|flag|picoCTF{r3j3ct_th3_du4l1ty_70bc61c4}|

|---|---|
|Accept|text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8|

|---|---|
|Accept-Encoding|gzip, deflate|
|Accept-Language|en-US,en;q=0.5|
|Cache-Control|no-cache|
|Connection|keep-alive|
|Host|mercury.picoctf.net:28916|
|Pragma|no-cache|
|Upgrade-Insecure-Requests|1|
|User-Agent|Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0|
```
## Notas Adicionales
- **GET** is used to request data from a specified resource.
- **HEAD** is almost identical to GET, but without the response body. In other words, if GET /users returns a list of users, then HEAD /users will make the same request but will not return the list of users.
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)