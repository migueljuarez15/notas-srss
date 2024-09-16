## Objetivo
What was I last working on? I remember writing a note to help me remember...
## Solución
```
┌──(kali㉿kali)-[~/Downloads]
└─$ unzip challenge.zip
Archive:  challenge.zip
   creating: drop-in/
  inflating: drop-in/message.txt     
   creating: drop-in/.git/
.   .   . 
   creating: drop-in/.git/logs/
  inflating: drop-in/.git/logs/HEAD  
   creating: drop-in/.git/logs/refs/
   creating: drop-in/.git/logs/refs/heads/
  inflating: drop-in/.git/logs/refs/heads/master  
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads]
└─$ ls -la
total 118520
drwxr-xr-x   5 kali kali      4096 Sep 16 18:29 .
drwx------  20 kali kali      4096 Sep 16 18:29 ..
drwxrwxr-x 121 kali kali     36864 May  3  2020 big-zip-files
-rw-rw-r--   1 kali kali   3182988 Sep 11 12:33 big-zip-files.zip
-rw-rw-r--   1 kali kali     17739 Mar 11  2024 challenge.zip
drwxr-xr-x   3 kali kali      4096 Mar 11  2024 drop-in
-rw-rw-r--   1 kali kali       349 Mar 15  2023 enc_flag
drwxrwxr-x   5 kali kali      4096 May 13  2022 files
-rw-rw-r--   1 kali kali   3995553 Aug  4  2023 files.zip
-rwxrwxr-x   1 kali kali 114091533 Sep 11 02:02 Obsidian-1.6.7.AppImage
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads]
└─$ cd drop-in  
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ ls -la
total 16
drwxr-xr-x 3 kali kali 4096 Mar 11  2024 .
drwxr-xr-x 5 kali kali 4096 Sep 16 18:29 ..
drwxr-xr-x 8 kali kali 4096 Mar 11  2024 .git
-rw-r--r-- 1 kali kali   87 Mar 11  2024 message.txt
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ cat message.txt
This is what I was working on, but I'd need to look at my commit history to know why...                                                                                                                  
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ git log      
commit 10228f3d6437701ef5aaac04213757031f30ebec (HEAD -> master)
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:24 2024 +0000

    picoCTF{t1m3m@ch1n3_8defe16a}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)