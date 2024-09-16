## Objetivo
I accidentally wrote the flag down. Good thing I deleted it!
## Solución
```
┌──(kali㉿kali)-[~/Downloads]
└─$ ls -la
total 114604
drwxr-xr-x   3 kali kali      4096 Sep 16 18:07 .
drwx------  20 kali kali      4096 Sep 16 18:07 ..
drwxrwxr-x 121 kali kali     36864 May  3  2020 big-zip-files
-rw-rw-r--   1 kali kali   3182988 Sep 11 12:33 big-zip-files.zip
-rw-rw-r--   1 kali kali     19196 Mar 11  2024 challenge.zip
-rwxrwxr-x   1 kali kali 114091533 Sep 11 02:02 Obsidian-1.6.7.AppImage
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads]
└─$ unzip challenge.zip                                         
Archive:  challenge.zip
   creating: drop-in/
   creating: drop-in/.git/
   creating: drop-in/.git/branches/
  inflating: drop-in/.git/description  
.   .   .
  inflating: drop-in/.git/logs/HEAD  
   creating: drop-in/.git/logs/refs/
   creating: drop-in/.git/logs/refs/heads/
  inflating: drop-in/.git/logs/refs/heads/master  
 extracting: drop-in/message.txt     
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads]
└─$ ls -la
total 114608
drwxr-xr-x   4 kali kali      4096 Sep 16 18:08 .
drwx------  20 kali kali      4096 Sep 16 18:07 ..
drwxrwxr-x 121 kali kali     36864 May  3  2020 big-zip-files
-rw-rw-r--   1 kali kali   3182988 Sep 11 12:33 big-zip-files.zip
-rw-rw-r--   1 kali kali     19196 Mar 11  2024 challenge.zip
drwxr-xr-x   3 kali kali      4096 Mar 11  2024 drop-in
-rwxrwxr-x   1 kali kali 114091533 Sep 11 02:02 Obsidian-1.6.7.AppImage
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads]
└─$ cd drop-in  
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ ls -la
total 16
drwxr-xr-x 3 kali kali 4096 Mar 11  2024 .
drwxr-xr-x 4 kali kali 4096 Sep 16 18:08 ..
drwxr-xr-x 8 kali kali 4096 Mar 11  2024 .git
-rw-r--r-- 1 kali kali   11 Mar 11  2024 message.txt
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ cat message.txt
TOP SECRET
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ git log                                                                                
commit 8dc51806c760dfdbb34b33a2008926d3d8e8ad49 (HEAD -> master)
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:06:17 2024 +0000

    remove sensitive info

commit 87b85d7dfb839b077678611280fa023d76e017b8
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:06:17 2024 +0000

    create flag
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ git show HEAD
commit 8dc51806c760dfdbb34b33a2008926d3d8e8ad49 (HEAD -> master)
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:06:17 2024 +0000

    remove sensitive info

diff --git a/message.txt b/message.txt
index bae247d..d552d1e 100644
--- a/message.txt
+++ b/message.txt
@@ -1 +1 @@
-picoCTF{s@n1t1z3_ea83ff2a}
+TOP SECRET
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)