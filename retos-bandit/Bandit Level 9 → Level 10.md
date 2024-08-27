## Objetivo
The password for the next level is stored in the file **data.txt** in one of the few human-readable strings, preceded by several ‘=’ characters.
## Datos de Acceso al Nivel
- **Puerto:** 2220
##### Se usará el usuario "bandit9":
- **Usuario:** bandit9
- **Contraseña:** 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
##### Después de conseguir la contraseña en el archivo "data.txt" y buscar la contraseña que sea algo humanamente-legible:
- **Usuario:** bandit10
- **Contraseña descubierta:** FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
## Solución
- ##### Inicio de sesión en el usuario "bandit9" para acceder al archivo "data.txt" y buscar la contraseña que sea algo humanamente-legible.
```
C:\Users\Miguel>ssh bandit9@bandit.labs.overthewire.org -p 2220
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit8@bandit.labs.overthewire.org's password:

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
bandit9@bandit:~$ ls -la
total 40
drwxr-xr-x  2 root     root     4096 Jul 17 15:57 .
drwxr-xr-x 70 root     root     4096 Jul 17 15:58 ..
-rw-r--r--  1 root     root      220 Mar 31 08:41 .bash_logout
-rw-r--r--  1 root     root     3771 Mar 31 08:41 .bashrc
-rw-r-----  1 bandit10 bandit9 19379 Jul 17 15:57 data.txt
-rw-r--r--  1 root     root      807 Mar 31 08:41 .profile
```

- ##### Uso de la instrucción "sort" para mostrar el contenido del archivo de forma ordenada. Se observa que contiene muchos caracteres especiales y caracteres normales.
```
bandit9@bandit:~$ sort data.txt
QM8i��e˘skr\z\]L! 1��UcIc#Rw掐6d?OvXZֲˎKu6*9?!'T0{K}J2;@b@M,eO{%s[>
05k()��3fvR_^D@��k_e+B!id*lkv27ʴR/v${u,\BDah:JWVC"AdH8Uۅ:b%`127tD~r9-
.   .   .
V;Ֆ*;.#
|諭<k!G#rP23/        .4˒Pm!(Ys^1(QЕt~ ݰo8}"I2Ӥі-Er4].nqtg8Wq{$"M~^u-omc]/ʔE0J9^.;64.3,F~V~!3^rG~nxדSLșwC=Boeډ"̺56v1ky0G8\[oTIY.jJy+o"h2ՙ^$CT2!}GϏlESuce0,%>fH<ؒ{yW4o#JwaK=CzY@R|u`
```

- ##### Uso de la instrucción "strings" para mostrar los caracteres normales en el archivo de texto.
```
bandit9@bandit:~$ strings data.txt
#mB}hF
3%A<.
~^u-
0J9^
;64.3
,F~V
.   .   .
)$,h
~"O>
%@Lq:
uR.}
```

- ##### Uso de la instrucción "strings" para solo mostrar los caracteres normales, también se hará uso de la instrucción "grep" para mostrar las líneas de texto que tengan la secuencia de caracteres "=" en el archivo.
```
bandit9@bandit:~$ strings data.txt | grep ===
\a!;========== the
========== passwordf
========== isc
========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```

- ##### Cierre de sesión del usuario "bandit9".
```
bandit9@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.
```
## Notas Adicionales
- **grep** - Muestra la línea del texto donde se buscó la palabra.
- **ls -la** - Lista archivos de de forma larga y detallada, al igual que todos los archivos (hasta ocultos).
- **strings** - Muestra las cadenas de caracteres en archivos de texto.
- **sort** - Ordena el archivo de forma alfabética.
## Referencias
- [OverTheWire](https://overthewire.org/wargames/bandit/bandit1.html)
- [Strings en Linux](https://infolinux.es/comando-strings-de-linux-obten-cadenas-de-texto-de-archivos-article-about-linux-command-strings-retrieve-text-strings-from-files/)