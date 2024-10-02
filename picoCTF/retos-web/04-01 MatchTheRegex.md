## Objetivo
How about trying to match a regular expression.
## Solución
- ##### Al entrar en la instancia e inspeccionar el código fuente de la página, observamos que hay una función llamada "send_request()", la cual hace que cualquier input valide que coincida con la Regex "/flag".
``` html
<!DOCTYPE html>
<html>

<head>
	<!-- <link rel="stylesheet" href="./index.css" /> -->
	<style>
		.heading {
			width: 100%;
			height: 40px;
			background-color: coral;
			padding-left: 10px;
			font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
		}

		.normal-form {
			text-align: center;
			margin-top: 5%;
		}

		#submit-but {
			border-radius: 0;
			width: 250px;
			height: 25px;

		}

		#name {
			width: 250px;
			height: 25px;
			background-color: rgb(241, 226, 206);
		}

		#sub-heading {
			color: brown;
		}
	</style>
</head>

<body>

	<h1 class="heading">PicoCTF</h1>
	<p></p>

	<div class="normal-form">
		<h2 id="sub-heading">Valid Input</h2>
		<form action="#" onsubmit="return send_request()">
			<input type="text" id="name" name="input" placeholder="Input text">
			<br>
			<br>
			<button id="submit-but" type="submit" id="submit-button">SUBMIT</button>
		</form>
	</div>
</body>
<script>
	function send_request() {
		let val = document.getElementById("name").value;
		// ^p.....F!?
		fetch(`/flag?input=${val}`)
			.then(res => res.text())
			.then(res => {
				const res_json = JSON.parse(res);
				alert(res_json.flag)
				return false;
			})
		return false;
	}

</script>

</html>
```

- ##### Al introducir los primeros caracteres "picoCTF{", obtenemos la bandera.
```
Flag: picoCTF{succ3ssfully_matchtheregex_2375af79}
```
## Notas Adicionales
- **Expresión Regular** (o **RegEx**, **Regular Expression**), como una cadena de texto genérica, que se usa a modo de patrón, y que sirve para localizar trozos de texto dentro de otro texto mayor.
## Referencias
- [PicoCTF](https://play.picoctf.org)