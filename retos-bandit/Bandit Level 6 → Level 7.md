## Objetivo
The password for the next level is stored **somewhere on the server** and has all of the following properties:

- owned by user bandit7
- owned by group bandit6
- 33 bytes in size
## Datos de Acceso al Nivel
- **Puerto:** 2220
##### Se usará el usuario "bandit6":
- **Usuario:** bandit6
- **Contraseña:** HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
##### Después de conseguir la contraseña en el archivo del usuario bandit7, del grupo bandit6 y de 33 bytes de de cualquier directorio:
- **Usuario:** bandit7
- **Contraseña descubierta:** morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
## Solución
- ##### Inicio de sesión en el usuario "bandit6" para acceder al archivo del usuario bandit7, del grupo bandit6 y de 33 bytes de tamaño de cualquier directorio.
```
C:\Users\Miguel>ssh bandit6@bandit.labs.overthewire.org -p 2220
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit6@bandit.labs.overthewire.org's password:

      ,----..            ,----,          .---.
     /   /   \         ,/   .`|         /. ./|
    /   .     :      ,`   .'  :     .--'.  ' ;
   .   /   ;.  \   ;    ;     /    /__./ \ : |
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :
  .   |  ' ' ' : `----'  |  |  \   ;  `      |
  '   ;  \; /  |     '   :  ;   .   \    .\  ;
   \   \  ',  /      |   |  '    \   \   ' \ |
    ;   :    /       '   :  |     :   '  |--"
     \   \ .'        ;   |.'       \   \ ;
  www. `---` ver     '---' he       '---" ire.org


Welcome to OverTheWire!

If you find any problems, please report them to the #wargames channel on
discord or IRC.

--[ Playing the games ]--

  This machine might hold several wargames.
  If you are playing "somegame", then:

    * USERNAMES are somegame0, somegame1, ...
    * Most LEVELS are stored in /somegame/.
    * PASSWORDS for each level are stored in /etc/somegame_pass/.

  Write-access to homedirectories is disabled. It is advised to create a
  working directory with a hard-to-guess name in /tmp/.  You can use the
  command "mktemp -d" in order to generate a random and hard to guess
  directory in /tmp/.  Read-access to both /tmp/ is disabled and to /proc
  restricted so that users cannot snoop on eachother. Files and directories
  with easily guessable or short names will be periodically deleted! The /tmp
  directory is regularly wiped.
  Please play nice:

    * don't leave orphan processes running
    * don't leave exploit-files laying around
    * don't annoy other players
    * don't post passwords or spoilers
    * again, DONT POST SPOILERS!
      This includes writeups of your solution on your blog or website!

--[ Tips ]--

  This machine has a 64bit processor and many security-features enabled
  by default, although ASLR has been switched off.  The following
  compiler flags might be interesting:

    -m32                    compile for 32bit
    -fno-stack-protector    disable ProPolice
    -Wl,-z,norelro          disable relro

  In addition, the execstack tool can be used to flag the stack as
  executable on ELF binaries.

  Finally, network-access is limited for most levels by a local
  firewall.

--[ Tools ]--

 For your convenience we have installed a few useful tools which you can find
 in the following locations:

    * gef (https://github.com/hugsy/gef) in /opt/gef/
    * pwndbg (https://github.com/pwndbg/pwndbg) in /opt/pwndbg/
    * peda (https://github.com/longld/peda.git) in /opt/peda/
    * gdbinit (https://github.com/gdbinit/Gdbinit) in /opt/gdbinit/
    * pwntools (https://github.com/Gallopsled/pwntools)
    * radare2 (http://www.radare.org/)

--[ More information ]--

  For more information regarding individual wargames, visit
  http://www.overthewire.org/wargames/

  For support, questions or comments, contact us on discord or IRC.

  Enjoy your stay!
```

- ##### Uso de la instrucción "ls -la" para mostrar el contenido del directorio actual. Se observa que no hay ningún archivo/directorio extra.
```
bandit6@bandit:~$ ls -la
total 20
drwxr-xr-x  2 root root 4096 Jul 17 15:56 .
drwxr-xr-x 70 root root 4096 Jul 17 15:58 ..
-rw-r--r--  1 root root  220 Mar 31 08:41 .bash_logout
-rw-r--r--  1 root root 3771 Mar 31 08:41 .bashrc
-rw-r--r--  1 root root  807 Mar 31 08:41 .profile
```

- ##### Uso de la instrucción "find" en el directorio actual de "bandit6" para buscar el archivo correspondiente. A eso se le suman las instrucciones "/ -user bandit7 -group bandit6 -size 33c" para buscar por el usuario y grupo, y que su peso sea de 33 bytes. El restante "2>/dev/null" es para tener un resultado más limpio, ya que nos muestran archivos basura, por lo que el comando evita esos archivos.
```
bandit6@bandit:~$ find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
/var/lib/dpkg/info/bandit7.password
```

- ##### Una vez teniendo la ruta y el nombre del archivo que contiene los requerimientos, tomaremos la información de ese archivo con la instrucción "cat".
```
bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```

- ##### Cierre de sesión del usuario "bandit6".
```
bandit6@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.
```
## Notas Adicionales
- **ls** - Listado de archivos.
- **cat** - Lista, combina y escribe el contenido de los archivos en la salida estándar.
- **find** - Busca archivos por instrucciones especificas en cualquier directorio existente.
- **ls -la** - Lista archivos de de forma larga y detallada, al igual que todos los archivos (hasta ocultos).
- **find -user** - Busca archivos por el usuario que lo posee.
- **find -group** - Busca archivos por el grupo que lo posee.
- **find - size** - Busca archivos por el tamaño de dicho archivo.
## Referencias
- [OverTheWire](https://overthewire.org/wargames/bandit/bandit1.html)
- [Comando Find en Linux](https://www.hostinger.mx/tutoriales/linux-comandos#25_Comando_find)