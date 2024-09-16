## Objetivo
Someone's commits seems to be preventing the program from working. Who is it?
## Solución
```
┌──(kali㉿kali)-[~]
└─$ cd Downloads
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads]
└─$ unzip challenge.zip
Archive:  challenge.zip
   creating: drop-in/
 extracting: drop-in/message.py      
   creating: drop-in/.git/
   creating: drop-in/.git/branches/
  inflating: drop-in/.git/description  
.   .   .     
 extracting: drop-in/.git/COMMIT_EDITMSG  
   creating: drop-in/.git/logs/
  inflating: drop-in/.git/logs/HEAD  
   creating: drop-in/.git/logs/refs/
   creating: drop-in/.git/logs/refs/heads/
  inflating: drop-in/.git/logs/refs/heads/master  
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads]
└─$ cd drop-in  
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ ls -la
total 16
drwxr-xr-x 3 kali kali 4096 Mar 11  2024 .
drwxr-xr-x 4 kali kali 4096 Sep 16 17:53 ..
drwxr-xr-x 8 kali kali 4096 Mar 11  2024 .git
-rw-r--r-- 1 kali kali   22 Mar 11  2024 message.py
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ git log > log.txt
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ cat log.txt | grep "picoCTF{"
Author: picoCTF{@sk_th3_1nt3rn_2c6bf174} <ops@picoctf.com>
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)