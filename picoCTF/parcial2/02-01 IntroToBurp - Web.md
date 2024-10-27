## Objetivo
Try [here](http://titan.picoctf.net:64521/) to find the flag.
## Solución
- ##### Al abrir la página, contestamos el formulario. Luego de eso nos pide un OTP de autentificación, pero vamos a interceptarlo con Burp, y luego de borrar la línea del otp y darle "Forward", tenemos lo siguiente:
```
Welcome, MKR you sucessfully bypassed the OTP request. Your Flag: picoCTF{#0TP_Bypvss_SuCc3$S_9090d63c}
```

- ##### Luego de pasar el OTP, obtenemos la bandera.
```
Flag: picoCTF{#0TP_Bypvss_SuCc3$S_9090d63c}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)