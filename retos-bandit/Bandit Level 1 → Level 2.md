## Objetivo
The password for the next level is stored in a file called **-** located in the home directory.
## Datos de Acceso al Nivel
- **Puerto:** 2220
##### Se usará el usuario "bandit1":
- **Usuario:** bandit1
- **Contraseña:** ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
##### Después de conseguir la contraseña en el archivo "-":
- **Usuario:** bandit2
- **Contraseña descubierta:** 263JGJPfgU6LtdEvgfWU1XP5yac29mFx
## Solución
- ##### Inicio de sesión en el usuario "bandit1" para acceder al archivo "-".
```
C:\Users\Miguel>ssh bandit1@bandit.labs.overthewire.org -p 2220
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit1@bandit.labs.overthewire.org's password:

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

- ##### Uso de la instrucción "cat" para revisar el contenido del archivo y revelar la contraseña, pero en esta ocasión es especial, se usan caracteres especiales antes del nombre del archivo (./) para no confundir al sistema, ya que, el guión (-) puede servir como una instrucción en la terminal.
```
bandit1@bandit:~$ ls
-
bandit1@bandit:~$ cat ./-
263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```

- ##### Cierre de sesión del usuario "bandit1".
```
bandit1@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.
```
## Notas Adicionales
- This type of approach has a lot of misunderstanding because using **-** as an argument refers to **STDIN/STDOUT** i.e **dev/stdin** or **dev/stdout** .So if you want to open this type of file you have to specify the full location of the file such as **./-** .For eg. , if you want to see what is in that file use **cat ./-**
- **ls** - Listado de archivos.
- **cat** - Lista, combina y escribe el contenido de los archivos en la salida estándar.
## Referencias
- [OverTheWire](https://overthewire.org/wargames/bandit/bandit1.html)
- [How To Open a Dashed Filename in Terminal](https://stackoverflow.com/questions/42187323/how-to-open-a-dashed-filename-using-terminal)