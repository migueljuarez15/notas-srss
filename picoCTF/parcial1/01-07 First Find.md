## Objetivo
Unzip this archive and find the file named 'uber-secret.txt'
## Solución
```
┌──(kali㉿kali)-[~/Downloads]
└─$ unzip files.zip    
Archive:  files.zip
   creating: files/
   creating: files/satisfactory_books/
   creating: files/satisfactory_books/more_books/
.   .   .
   creating: files/acceptable_books/more_books/
  inflating: files/acceptable_books/more_books/40723.txt.utf-8  
  inflating: files/acceptable_books/17880.txt.utf-8  
  inflating: files/acceptable_books/17879.txt.utf-8  
  inflating: files/14789.txt.utf-8   
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads]
└─$ ls -la
total 118516
drwxr-xr-x   5 kali kali      4096 Sep 16 18:12 .
drwx------  20 kali kali      4096 Sep 16 18:07 ..
drwxrwxr-x 121 kali kali     36864 May  3  2020 big-zip-files
-rw-rw-r--   1 kali kali   3182988 Sep 11 12:33 big-zip-files.zip
-rw-rw-r--   1 kali kali     19196 Mar 11  2024 challenge.zip
drwxr-xr-x   3 kali kali      4096 Mar 11  2024 drop-in
drwxrwxr-x   5 kali kali      4096 May 13  2022 files
-rw-rw-r--   1 kali kali   3995553 Aug  4  2023 files.zip
-rwxrwxr-x   1 kali kali 114091533 Sep 11 02:02 Obsidian-1.6.7.AppImage
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads]
└─$ cat files.zip
PK
���Tfiles/UT    ��~b��~bux
                          ��PK
b��Tfiles/satisfactory_books/UT 7�~b:�~bux
                                          ��PK
r��T$files/satisfactory_books/more_books/UT     W�~bX�~bux
.   .   .
P��T▒�Ar▒,files/acceptable_books/UT8�~bux
                                         ��PK
k��T"▒�A�▒,files/acceptable_books/more_books/UTi�~bux
                                                     ��PaD�T0�,�(�1▒��files/acceptable_books/more_books/40723.txt.utf-8UT�Z]bux
&▒���C-files/acceptable_books/17880.txt.utf-8UT��wbux
&▒���b2files/acceptable_books/17879.txt.utf-8UT��wbux��PQX�T��mN+�
                                                     ��P�;�Tc.@�_S�▒��3�7files/14789.txt.utf-8UTsXvbux
                                                                                                      ��PKM  >�< 

┌──(kali㉿kali)-[~/Downloads]
└─$ strings files.zip                                                                                            
files/UT
~bux
files/satisfactory_books/UT
~bux
files/satisfactory_books/more_books/UT
~bux
files/satisfactory_books/more_books/37121.txt.utf-8UT
~bux
?}l6Mm
|yS}
euy^
_VWo
.   .   .
^t5;
%hvv
bE(j
s| uAv
P-"M
&3NKCS 
files/UT
~bux
files/satisfactory_books/UT
~bux
files/satisfactory_books/more_books/UT
~bux
files/satisfactory_books/more_books/37121.txt.utf-8UT
[bux
files/satisfactory_books/23765.txt.utf-8UT
{bux
files/satisfactory_books/16021.txt.utf-8UT
vbux
files/13771.txt.utf-8UT
ubux
files/adequate_books/UT
~bux
files/adequate_books/more_books/UT
~bux
files/adequate_books/more_books/.secret/UT
~bux
files/adequate_books/more_books/.secret/deeper_secrets/UT
~bux
files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/UT
~bux
files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txtUT
~bux
files/adequate_books/more_books/1023.txt.utf-8UT
Qnbux
Bs'E@.
files/adequate_books/46804-0.txtUT
files/adequate_books/44578.txt.utf-8UT
_bux
files/acceptable_books/UT
~bux
files/acceptable_books/more_books/UT
~bux
files/acceptable_books/more_books/40723.txt.utf-8UT
Z]bux
files/acceptable_books/17880.txt.utf-8UT
wbux
files/acceptable_books/17879.txt.utf-8UT
wbux
files/14789.txt.utf-8UT
sXvbux
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads]
└─$ strings files.zip | grep "picoCTF"
picoCTF{f1nd_15_f457_ab443fd1}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)