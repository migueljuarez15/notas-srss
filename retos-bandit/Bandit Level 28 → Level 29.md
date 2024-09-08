## Objetivo
There is a git repository at `ssh://bandit28-git@localhost/home/bandit28-git/repo` via the port `2220`. The password for the user `bandit28-git` is the same as for the user `bandit28`.

Clone the repository and find the password for the next level.
## Datos de Acceso al Nivel
- **Puerto:** 2220
##### Se usará el usuario "bandit28":
- **Usuario:** bandit28
- **Contraseña:** Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN
##### Después de conseguir la contraseña:
- **Usuario:** bandit29
- **Contraseña descubierta:** 4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7
## Solución
```
bandit28@bandit:~$ mktemp -d
/tmp/tmp.bwMfyJLkDN
bandit28@bandit:~$ cd /tmp/tmp.bwMfyJLkDN
bandit28@bandit:/tmp/tmp.bwMfyJLkDN$ git clone ssh://bandit28-git@localhost:2220/home/bandit28-git/repo
Cloning into 'repo'...
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit28/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit27/.ssh/known_hosts).
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _ | '_ \ / _ | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames
bandit28-git@localhost's password:
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (3/3), done.
bandit28@bandit:/tmp/tmp.bwMfyJLkDN$ ls
repo
bandit28@bandit:/tmp/tmp.bwMfyJLkDN$ cat repo
cat: repo: Is a directory
bandit28@bandit:/tmp/tmp.bwMfyJLkDN$ cd repo
bandit28@bandit:/tmp/tmp.bwMfyJLkDN/repo$ ls
README.md
bandit28@bandit:/tmp/tmp.bwMfyJLkDN/repo$ cat README.md
# Bandit Notes
Some notes for level29 of bandit.

## credentials

- username: bandit29
- password: xxxxxxxxxx

bandit28@bandit:/tmp/tmp.bwMfyJLkDN/repo$ git show
commit 8cbd1e08d1879415541ba19ddee3579e80e3f61a (HEAD -> master, origin/master, origin/HEAD)
Author: Morla Porla <morla@overthewire.org>
Date:   Wed Jul 17 15:57:30 2024 +0000

    fix info leak

diff --git a/README.md b/README.md
index d4e3b74..5c6457b 100644
--- a/README.md
+++ b/README.md
@@ -4,5 +4,5 @@ Some notes for level29 of bandit.
 ## credentials

 - username: bandit29
-- password: 4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7
+- password: xxxxxxxxxx
```

- ##### Cierre de sesión del usuario "bandit28".
```
bandit28@bandit:/tmp/tmp.bwMfyJLkDN/repo$ exit
logout
Connection to bandit.labs.overthewire.org closed.
```
## Notas Adicionales
- **git show** - El comando se utiliza para ver los cambios de una confirmación específica.
## Referencias
- [OverTheWire](https://overthewire.org/wargames/bandit/bandit1.html)