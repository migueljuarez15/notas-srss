## Objetivo
The password for the next level is stored in the only human-readable file in the **inhere** directory. Tip: if your terminal is messed up, try the “reset” command.
## Datos de Acceso al Nivel
- **Puerto:** 2220
##### Se usará el usuario "bandit4":
- **Usuario:** bandit4
- **Contraseña:** 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
##### Después de conseguir la contraseña en el archivo humanamente-legible del directorio "inhere":
- **Usuario:** bandit5
- **Contraseña descubierta:** 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
## Solución
- ##### Inicio de sesión en el usuario "bandit4" para acceder al archivo humanamente-legible del directorio "inhere".
```
C:\Users\Miguel>ssh bandit4@bandit.labs.overthewire.org -p 2220
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit4@bandit.labs.overthewire.org's password:

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

- ##### Uso de la instrucción "ls" para mostrar el directorio que tenemos que usar, y luego usamos "cd" para cambiar de directorio.
```
bandit4@bandit:~$ ls
inhere
bandit4@bandit:~$ cd inhere
```

- ##### Uso de la instrucción "ls" en el directorio "inhere", y muestra el nombre de todos los archivos existentes.
```
bandit4@bandit:~/inhere$ ls
-file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file09
```

- ##### Uso de la instrucción "file" para revisar de que tipo son los archivos.
```
bandit4@bandit:~/inhere$ file ./*
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
```

- ##### Se observa que el único archivo humanamente-legible es el archivo "-file07" al ser ASCII, por lo que tomaremos la información solo de ese archivo con la instrucción "cat".
```
bandit4@bandit:~/inhere$ cat ./-file07
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```

- ##### Cierre de sesión del usuario "bandit4".
```
bandit4@bandit:~/inhere$ exit
logout
Connection to bandit.labs.overthewire.org closed.
```
## Notas Adicionales
- This type of approach has a lot of misunderstanding because using **-** as an argument refers to **STDIN/STDOUT** i.e **dev/stdin** or **dev/stdout** .So if you want to open this type of file you have to specify the full location of the file such as **./-** .For eg. , if you want to see what is in that file use **cat ./-**
- **cd** - Cambiar de directorios.
- **ls** - Listado de archivos.
- **cat** - Lista, combina y escribe el contenido de los archivos en la salida estándar.
## Referencias
- [OverTheWire](https://overthewire.org/wargames/bandit/bandit1.html)
- [How To Open a Dashed Filename in Terminal](https://stackoverflow.com/questions/42187323/how-to-open-a-dashed-filename-using-terminal)