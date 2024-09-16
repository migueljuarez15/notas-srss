## Objetivo
My team has been working very hard on new features for our flag printing program! I wonder how they'll work together?
## Solución
```
┌──(kali㉿kali)-[~/Downloads]
└─$ unzip challenge.zip.1
Archive:  challenge.zip.1
replace drop-in/.git/description? [y]es, [n]o, [A]ll, [N]one, [r]ename: A
  inflating: drop-in/.git/description  
  inflating: drop-in/.git/hooks/applypatch-msg.sample  
  inflating: drop-in/.git/hooks/commit-msg.sample  
.   .   .
  inflating: drop-in/.git/logs/refs/heads/feature/part-1  
  inflating: drop-in/.git/logs/refs/heads/feature/part-2  
  inflating: drop-in/.git/logs/refs/heads/feature/part-3  
  inflating: drop-in/flag.py         
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads]
└─$ ls -la
total 114900
drwxr-xr-x   4 kali kali      4096 Sep 16 17:57 .
drwx------  20 kali kali      4096 Sep 16 17:56 ..
drwxrwxr-x 121 kali kali     36864 May  3  2020 big-zip-files
-rw-rw-r--   1 kali kali   3182988 Sep 11 12:33 big-zip-files.zip
-rw-rw-r--   1 kali kali    294455 Mar 11  2024 challenge.zip
-rw-rw-r--   1 kali kali     24474 Mar 11  2024 challenge.zip.1
drwxr-xr-x   3 kali kali      4096 Sep 16 17:57 drop-in
-rwxrwxr-x   1 kali kali 114091533 Sep 11 02:02 Obsidian-1.6.7.AppImage
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads]
└─$ cd drop-in    
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ ls -la
total 96
drwxr-xr-x 3 kali kali  4096 Sep 16 17:57 .
drwxr-xr-x 4 kali kali  4096 Sep 16 17:57 ..
-rw-r--r-- 1 kali kali    30 Mar 11  2024 flag.py
drwxr-xr-x 8 kali kali  4096 Sep 16 17:57 .git
-rw-rw-r-- 1 kali kali 75836 Sep 16 17:53 log.txt
-rw-r--r-- 1 kali kali    22 Mar 11  2024 message.py
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ cat flag.py                  
print("Printing the flag...")
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ git branch 
  feature/part-1
  feature/part-2
  feature/part-3
* main
  master
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ git checkout feature/part-1
Switched to branch 'feature/part-1'
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ cat flag.py
print("Printing the flag...")
print("picoCTF{t3@mw0rk_", end='')                                                                                                                  
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ git checkout feature/part-2
Switched to branch 'feature/part-2'
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ cat flag.py                
print("Printing the flag...")

print("m@k3s_th3_dr3@m_", end='')                                                                                                                  
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ git checkout feature/part-3 
Switched to branch 'feature/part-3'
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads/drop-in]
└─$ cat flag.py                
print("Printing the flag...")

print("w0rk_2c91ca76}")

Flag: picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_w0rk_2c91ca76}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)