## Objetivo
I sent out 2 invitations to all of my friends for my birthday! I'll know if they get stolen because the two invites look similar, and they even have the same md5 hash, but they are slightly different! You wouldn't believe how long it took me to find a collision. Anyway, see if you're invited by submitting 2 PDFs to my website. [http://mercury.picoctf.net:63578/](http://mercury.picoctf.net:63578/)
## Solución
- ##### Al abrir la página, nos pide que proporcionemos las invitaciones en formato PDF para ver si estamos invitados, si subimos cualquier PDF no nos deja, por lo que usaremos dos archivos a los que le cambiaremos la extensión ".exe" a ".pdf", los cuales ambos tiene el mismo hash MD5.
```
Windows version:
	hello.exe. MD5 Sum: cdc47d670159eef60916ca03a9d4a007
	erase.exe. MD5 Sum: cdc47d670159eef60916ca03a9d4a007
```

- ##### Al subir los archivos modificados, el sitio nos muestra el código fuente de este mismo.
```html
<?php  
  
if (isset($_POST["submit"])) {    $type1 = $_FILES["file1"]["type"];    $type2 = $_FILES["file2"]["type"];    $size1 = $_FILES["file1"]["size"];    $size2 = $_FILES["file2"]["size"];    $SIZE_LIMIT = 18 * 1024;  
  
    if (($size1 < $SIZE_LIMIT) && ($size2 < $SIZE_LIMIT)) {  
        if (($type1 == "application/pdf") && ($type2 == "application/pdf")) {            $contents1 = file_get_contents($_FILES["file1"]["tmp_name"]);            $contents2 = file_get_contents($_FILES["file2"]["tmp_name"]);  
  
            if ($contents1 != $contents2) {  
                if (md5_file($_FILES["file1"]["tmp_name"]) == md5_file($_FILES["file2"]["tmp_name"])) {                    highlight_file("index.php");  
                    die();  
                } else {  
                    echo "MD5 hashes do not match!";  
                    die();  
                }  
            } else {  
                echo "Files are not different!";  
                die();  
            }  
        } else {  
            echo "Not a PDF!";  
            die();  
        }  
    } else {  
        echo "File too large!";  
        die();  
    }  
}  
  
// FLAG: picoCTF{c0ngr4ts_u_r_1nv1t3d_5c8c5ce2}  
  
?>  
<!DOCTYPE html>  
<html lang="en">  
  
<head>  
    <title>It is my Birthday</title>  
  
  
    <link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css" rel="stylesheet">  
  
    <link href="https://getbootstrap.com/docs/3.3/examples/jumbotron-narrow/jumbotron-narrow.css" rel="stylesheet">  
  
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>  
  
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>  
  
  
</head>  
  
<body>  
  
    <div class="container">  
        <div class="header">  
            <h3 class="text-muted">It is my Birthday</h3>  
        </div>  
        <div class="jumbotron">  
            <p class="lead"></p>  
            <div class="row">  
                <div class="col-xs-12 col-sm-12 col-md-12">  
                    <h3>See if you are invited to my party!</h3>  
                </div>  
            </div>  
            <br/>  
            <div class="upload-form">  
                <form role="form" action="/index.php" method="post" enctype="multipart/form-data">  
                <div class="row">  
                    <div class="form-group">  
                        <input type="file" name="file1" id="file1" class="form-control input-lg">  
                        <input type="file" name="file2" id="file2" class="form-control input-lg">  
                    </div>  
                </div>  
                <div class="row">  
                    <div class="col-xs-12 col-sm-12 col-md-12">  
                        <input type="submit" class="btn btn-lg btn-success btn-block" name="submit" value="Upload">  
                    </div>  
                </div>  
                </form>  
            </div>  
        </div>  
    </div>  
    <footer class="footer">  
        <p>&copy; PicoCTF</p>  
    </footer>  
  
</div>  
  
<script>  
$(document).ready(function(){  
    $(".close").click(function(){  
        $("myAlert").alert("close");  
    });  
});  
</script>  
</body>  
  
</html>
```

- ##### Luego de ver el código fuente, obtenemos la bandera.
```
Flag: picoCTF{c0ngr4ts_u_r_1nv1t3d_5c8c5ce2}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)