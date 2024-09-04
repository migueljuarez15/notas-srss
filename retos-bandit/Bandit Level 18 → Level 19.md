## Objetivo
The password for the next level is stored in a file **readme** in the homedirectory. Unfortunately, someone has modified **.bashrc** to log you out when you log in with SSH.
## Datos de Acceso al Nivel
- **Puerto:** 2220
##### Se usará el usuario "bandit18":
- **Usuario:** bandit18
- **Contraseña:** x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
##### Después de conseguir la contraseña:
- **Usuario:** bandit19
- **Contraseña descubierta:** cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8
## Solución
```
bandit18@bandit.labs.overthewire.org's password:
id
uid=11018(bandit18) gid=11018(bandit18) groups=11018(bandit18)
ls
readme
cat readme
cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8
exit
```
## Notas Adicionales
- SSH permite que al conectarte puedas ejecutar una serie de comandos.
## Referencias
- [OverTheWire](https://overthewire.org/wargames/bandit/bandit1.html)
- [SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)