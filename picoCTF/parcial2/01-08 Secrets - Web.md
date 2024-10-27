## Objetivo
We have several pages hidden. Can you find the one with the flag?
## Solución
- ##### Inspeccionamos el código fuente de la página, el cual vemos que tiene un directorio llamado "secret".
```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <meta
      name="viewport"
      content="width=device-width, initial-scale=1, shrink-to-fit=no"
    />
    <meta name="description" content="" />
    <!-- Bootstrap core CSS -->
    <link href="vendor/bootstrap/css/bootstrap.min.css" rel="stylesheet" />
    <!-- title -->
    <title>home</title>
    <!-- css -->
    <link href="secret/assets/index.css" rel="stylesheet" />
  </head>
  <body>
    <!-- ***** Header Area Start ***** -->
    <div class="topnav">
      <a class="active" href="#home">Home</a>
      <a href="about.html">About</a>
      <a href="contact.html">Contact</a>
    </div>

    <div class="imgcontainer">
      <img
        src="secret/assets/DX1KYM.jpg"
        alt="https://www.alamy.com/security-safety-word-cloud-concept-image-image67649784.html"
        class="responsive"
      />
      <div class="top-left">
        <h1>If security wasn't your job, would you do it as a hobby?</h1>
      </div>
    </div>
  </body>
</html>
```

- ##### Seguiremos cada directorio así:
```
http://saturn.picoctf.net:56457/secret/hidden/superhidden/
```

- ##### Una vez llegado a "superhidden", obtenemos la bandera.
```
Flag: picoCTF{succ3ss_@h3n1c@10n_790d2615}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)