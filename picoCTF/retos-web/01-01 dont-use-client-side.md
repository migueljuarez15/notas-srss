## Objetivo
Can you break into this super secure portal? `https://jupiter.challenges.picoctf.org/problem/17682/` ([link](https://jupiter.challenges.picoctf.org/problem/17682/)) or http://jupiter.challenges.picoctf.org:17682
## Solución
- ##### Se inspecciona el código fuente de la página para buscar posibles fallos. Y como se logra observar, se quedó parte importante del código del lado del cliente, ya que la función "verify()" no debería ser accedida desde el código principal.
``` bash
<html>
<head>
<title>Secure Login Portal</title>
</head>
<body bgcolor=blue>
<!-- standard MD5 implementation -->
<script type="text/javascript" src="md5.js"></script>

<script type="text/javascript">
  function verify() {
    checkpass = document.getElementById("pass").value;
    split = 4;
    if (checkpass.substring(0, split) == 'pico') {
      if (checkpass.substring(split*6, split*7) == '706c') {
        if (checkpass.substring(split, split*2) == 'CTF{') {
         if (checkpass.substring(split*4, split*5) == 'ts_p') {
          if (checkpass.substring(split*3, split*4) == 'lien') {
            if (checkpass.substring(split*5, split*6) == 'lz_b') {
              if (checkpass.substring(split*2, split*3) == 'no_c') {
                if (checkpass.substring(split*7, split*8) == '5}') {
                  alert("Password Verified")
                  }
                }
              }
      
            }
          }
        }
      }
    }
    else {
      alert("Incorrect password");
    }
    
  }
</script>
<div style="position:relative; padding:5px;top:50px; left:38%; width:350px; height:140px; background-color:yellow">
<div style="text-align:center">
<p>This is the secure login portal</p>
<p>Enter valid credentials to proceed</p>
<form action="index.html" method="post">
<input type="password" id="pass" size="8" />
<br/>
<input type="submit" value="verify" onclick="verify(); return false;" />
</form>
</div>
</div>
</body>
</html>
```

- ##### Se puede apreciar que la contraseña del sitio es la bandera que estamos buscando, por lo que armaremos la bandera usando la lógica de que la variable "split" es igual a 4, y nos iremos guiando por sus multiplicaciones.
``` bash
function verify() {
    checkpass = document.getElementById("pass").value;
    split = 4;
    if (checkpass.substring(0, split) == 'pico') { --PARTE 1
      if (checkpass.substring(split*6, split*7) == '706c') { --PARTE 7
        if (checkpass.substring(split, split*2) == 'CTF{') { --PARTE 2
         if (checkpass.substring(split*4, split*5) == 'ts_p') { -PARTE 5
          if (checkpass.substring(split*3, split*4) == 'lien') { --PARTE 4
            if (checkpass.substring(split*5, split*6) == 'lz_b') { --PARTE 6
              if (checkpass.substring(split*2, split*3) == 'no_c') { --PARTE 3
                if (checkpass.substring(split*7, split*8) == '5}') { --PARTE 8
                  alert("Password Verified")
                  }
                }
              }
      
            }
          }
        }
      }
    }
    else {
      alert("Incorrect password");
    }
  }
```

- ##### Se arma la bandera siguiendo la lógica de la función "verify()".
```
Flag: picoCTF{no_clients_plz_b706c5}
```
## Notas Adicionales
- Es importante tener un código bien organizado, y poner muchas de las cosas del "frontend" en archivos más separados y propios, para evitar explotaciones de funciones importantes.
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)