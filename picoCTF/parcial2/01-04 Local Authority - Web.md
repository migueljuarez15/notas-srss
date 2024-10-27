## Objetivo
Can you get the flag?
## Solución
- ##### Inspeccionamos el código fuente, no obtenemos mucha información más que instrucciones de que debe contener la contraseña.
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="style.css">
    <title>Secure Customer Portal</title>
  </head>
  <body>

    <h1>Secure Customer Portal</h1>
    
   <p>Only letters and numbers allowed for username and password.</p>
    
    <form role="form" action="login.php" method="post">
      <input type="text" name="username" placeholder="Username" required 
       autofocus></br>
      <input type="password" name="password" placeholder="Password" required>
      <button type="submit" name="login">Login</button>
    </form>
  </body>
</html>
```

- ##### Al intentar iniciar sesión con datos erróneos, vemos que se genera un archivo JS, el cual contiene los datos correctos.
```js
function checkPassword(username, password)
{
  if( username === 'admin' && password === 'strongPassword098765' )
  {
    return true;
  }
  else
  {
    return false;
  }
}
```

- ##### Al introducir los datos correctos de inicio de sesión, obtenemos la bandera.
```
Flag: picoCTF{j5_15_7r4n5p4r3n7_a8788e61}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)