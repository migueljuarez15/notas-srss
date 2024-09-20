## Objetivo
Can you find the robots? `https://jupiter.challenges.picoctf.org/problem/56830/` ([link](https://jupiter.challenges.picoctf.org/problem/56830/)) or http://jupiter.challenges.picoctf.org:56830
## Solución
- ##### Ingresando al sitio web, vemos lo siguiente y no hay nada en el código fuente.
```
Welcome
Where are the robots?
```

- ##### Pondremos en la URL lo siguiente:
```
https://jupiter.challenges.picoctf.org/problem/56830/robots.txt
```

- ##### Y la página nos mostrará esto:
```
User-agent: *
Disallow: /1bb4c.html
```

- ##### Una vez copiado el link de html que hallamos en el archivo "robots.txt", lo pegaremos una vez más en la URL, y así obtenemos la bandera.
```
Flag: picoCTF{ca1cu1at1ng_Mach1n3s_1bb4c}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)