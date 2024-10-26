## Objetivo
Someone might have hidden the password in the trace file. Find the key to unlock [this file](https://artifacts.picoctf.net/c/496/flag.zip). [This tracefile](https://artifacts.picoctf.net/c/496/dump.pcap) might be good to analyze.
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Forensics/FindAndOpen]
└─$ wget https://artifacts.picoctf.net/c/496/flag.zip        
--2024-10-26 01:45:06--  https://artifacts.picoctf.net/c/496/flag.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.61, 3.161.55.64, 3.161.55.100, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.61|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 231 [application/octet-stream]
Saving to: ‘flag.zip’

flag.zip                     100%[============================================>]     231  --.-KB/s    in 0s      

2024-10-26 01:45:07 (268 MB/s) - ‘flag.zip’ saved [231/231]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/FindAndOpen]
└─$ wget https://artifacts.picoctf.net/c/496/dump.pcap
--2024-10-26 01:45:19--  https://artifacts.picoctf.net/c/496/dump.pcap
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.26, 3.161.55.100, 3.161.55.64, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.26|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7413 (7.2K) [application/octet-stream]
Saving to: ‘dump.pcap’

dump.pcap                    100%[============================================>]   7.24K  --.-KB/s    in 0s      

2024-10-26 01:45:20 (220 MB/s) - ‘dump.pcap’ saved [7413/7413]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/FindAndOpen]
└─$ unzip flag.zip       
Archive:  flag.zip
[flag.zip] flag password:                                                                                                                   
┌──(kali㉿kali)-[~/picoCTF/Forensics/FindAndOpen]
└─$ wireshark dump.pcap
```

- ##### Obtenemos esto en el archivo ".pcap", el cual nos da la contraseña para extraer el archivo ".zip", averiguaremos cual es.
```
Flying on Ethernet secret: Is this the flag
iBwaWNvQ1RGe1Could the flag have been splitted?
AABBHHPJGTFRLKVGhpcyBpcyB0aGUgc2VjcmV0OiBwaWNvQ1RGe1IzNERJTkdfTE9LZF8=
PBwaWUvQ1RGesabababkjaASKBKSBACVVAVSDDSSSSDSKJBJS
PBwaWUvQ1RGe1Maybe try checking the other file
```

- ##### Decodificaremos por base64 una de las cadenas que se nos dio en el archivo, y le pondremos las letras "aa" al inicio de la cadena.
```
┌──(kali㉿kali)-[~/picoCTF/Forensics/FindAndOpen]
└─$ echo aaAABBHHPJGTFRLKVGhpcyBpcyB0aGUgc2VjcmV0OiBwaWNvQ1RGe1IzNERJTkdfTE9LZF8= | base64 -di
i��<���This is the secret: picoCTF{R34DING_LOKd_                                                                                                   
┌──(kali㉿kali)-[~/picoCTF/Forensics/FindAndOpen]
└─$ unzip flag.zip
Archive:  flag.zip
[flag.zip] flag password: picoCTF{R34DING_LOKd_
 extracting: flag                    
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/FindAndOpen]
└─$ ls                  
dump.pcap  flag  flag.zip
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/FindAndOpen]
└─$ cat flag            
picoCTF{R34DING_LOKd_fil56_succ3ss_5ed3a878}
```

- ##### Una vez extraído el archivo, obtenemos la bandera.
```
Flag: picoCTF{R34DING_LOKd_fil56_succ3ss_5ed3a878}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)