## Objetivo
The factory is hiding things from all of its users. Can you login as Joe and find what they've been looking at? `https://jupiter.challenges.picoctf.org/problem/44573/` ([link](https://jupiter.challenges.picoctf.org/problem/44573/)) or http://jupiter.challenges.picoctf.org:44573
## Solución
- ##### Se inspecciona el código fuente de la página para buscar la cookie de inicio de sesión, y obtenemos la siguiente cookie.
```
|---|---|---|---|---|---|---|---|---|---|---|---|
|admin|False|jupiter.challenges.picoctf.org|/problem/44573|Session|9||||||Mediu|
```

- ##### Se usa un editor de cookies para cambiar el valor a "True".
```
|---|---|---|---|---|---|---|---|---|---|---|---|
|admin|True|jupiter.challenges.picoctf.org|/problem/44573|Session|9||||||Mediu|
```

- ##### Recargando la página, obtenemos la bandera.
```
Flag: picoCTF{th3_c0nsp1r4cy_l1v3s_0c98aacc}
```
## Notas Adicionales
- Las cookies puedes ser editadas.
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)