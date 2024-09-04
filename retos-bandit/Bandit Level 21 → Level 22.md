## Objetivo
A program is running automatically at regular intervals from **cron**, the time-based job scheduler. Look in **/etc/cron.d/** for the configuration and see what command is being executed.
## Datos de Acceso al Nivel
- **Puerto:** 2220
##### Se usará el usuario "bandit21":
- **Usuario:** bandit21
- **Contraseña:** EeoULMCra2q0dSkYj561DX7s1CpBuOBt
##### Después de conseguir la contraseña:
- **Usuario:** bandit22
- **Contraseña descubierta:** tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q
## Solución
```
bandit21@bandit:~$ ls -la
total 24
drwxr-xr-x  2 root     root     4096 Jul 17 15:57 .
drwxr-xr-x 70 root     root     4096 Jul 17 15:58 ..
-rw-r--r--  1 root     root      220 Mar 31 08:41 .bash_logout
-rw-r--r--  1 root     root     3771 Mar 31 08:41 .bashrc
-r--------  1 bandit21 bandit21   33 Jul 17 15:57 .prevpass
-rw-r--r--  1 root     root      807 Mar 31 08:41 .profile
bandit21@bandit:~$ cron
cron: can't open or create /var/run/crond.pid: Permission denied
bandit21@bandit:~$ whoami
bandit21
bandit21@bandit:~$ ./etc/cron.d
-bash: ./etc/cron.d: No such file or directory
bandit21@bandit:~$ ./etc/cron.d/
-bash: ./etc/cron.d/: No such file or directory
bandit21@bandit:~$ ls /etc/cron.d/
cronjob_bandit22  cronjob_bandit24  otw-tmp-dir
cronjob_bandit23  e2scrub_all       sysstat
bandit21@bandit:~$ ls -la  /etc/cron.d/
total 44
drwxr-xr-x   2 root root  4096 Jul 17 15:59 .
drwxr-xr-x 121 root root 12288 Aug  1 14:49 ..
-rw-r--r--   1 root root   120 Jul 17 15:57 cronjob_bandit22
-rw-r--r--   1 root root   122 Jul 17 15:57 cronjob_bandit23
-rw-r--r--   1 root root   120 Jul 17 15:57 cronjob_bandit24
-rw-r--r--   1 root root   201 Apr  8 14:38 e2scrub_all
-rwx------   1 root root    52 Jul 17 15:59 otw-tmp-dir
-rw-r--r--   1 root root   102 Mar 31 00:06 .placeholder
-rw-r--r--   1 root root   396 Jan  9  2024 sysstat
bandit21@bandit:~$ cat /etc/cron.d/cronjob_bandit22
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
bandit21@bandit:~$ cat /usr/bin/cronjob_bandit22.sh
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
bandit21@bandit:~$ cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q
```

- ##### Cierre de sesión del usuario "bandit21".
```
bandit21@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.
```
## Notas Adicionales
## Referencias
- [OverTheWire](https://overthewire.org/wargames/bandit/bandit1.html)