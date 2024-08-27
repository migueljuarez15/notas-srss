## Objetivo
The password for the next level is stored in the file **data.txt** next to the word **millionth**.
## Datos de Acceso al Nivel
- **Puerto:** 2220
##### Se usará el usuario "bandit7":
- **Usuario:** bandit7
- **Contraseña:** morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
##### Después de conseguir la contraseña en el archivo "data.txt" y buscar la contraseña al lado de la palabra "millionth":
- **Usuario:** bandit8
- **Contraseña descubierta:** dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
## Solución
- ##### Inicio de sesión en el usuario "bandit7" para acceder al archivo "data.txt" y buscar la contraseña al lado de la palabra "millionth".
```
C:\Users\Miguel>ssh bandit7@bandit.labs.overthewire.org -p 2220
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit7@bandit.labs.overthewire.org's password:

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

- ##### Uso de la instrucción "ls -la" para mostrar el contenido del directorio actual.
```
bandit7@bandit:~$ ls -la
total 4108
drwxr-xr-x  2 root    root       4096 Jul 17 15:57 .
drwxr-xr-x 70 root    root       4096 Jul 17 15:58 ..
-rw-r--r--  1 root    root        220 Mar 31 08:41 .bash_logout
-rw-r--r--  1 root    root       3771 Mar 31 08:41 .bashrc
-rw-r-----  1 bandit8 bandit7 4184396 Jul 17 15:57 data.txt
-rw-r--r--  1 root    root        807 Mar 31 08:41 .profile
```

- ##### Uso de la instrucción "wc -l" para mostrar la dimensión de líneas de texto del archivo.
```
bandit7@bandit:~$ wc -l data.txt
98567 data.txt
```

- ##### Uso de la instrucción "grep" para mostrar la línea de texto que tenga la palabra "millionth" en el archivo. La instrucción "grep -n" muestra el numero de línea que es en el archivo.
```
bandit7@bandit:~$ grep millionth data.txt
millionth       dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
bandit7@bandit:~$ grep -n millionth data.txt
86483:millionth dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```

- ##### Cierre de sesión del usuario "bandit7".
```
bandit7@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.
```
## Notas Adicionales
- **ls** - Listado de archivos.
- **grep** - Muestra la línea del texto donde se buscó la palabra.
- **ls -la** - Lista archivos de de forma larga y detallada, al igual que todos los archivos (hasta ocultos).
- **wc -l** - Cuenta el numero de líneas que tiene un archivo de texto.
- **grep -n** - Muestra el número de línea y la línea del texto donde se buscó la palabra.
## Referencias
- [OverTheWire](https://overthewire.org/wargames/bandit/bandit1.html)
- [Comando Grep en Linux](https://www.hostinger.mx/tutoriales/linux-comandos#15_Comando_grep)