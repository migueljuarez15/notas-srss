## Objetivo
I wonder what this really is... [enc](https://mercury.picoctf.net/static/e47483f88b12f2ab0c46315afc12f64d/enc) `''.join([chr((ord(flag[i]) << 8) + ord(flag[i + 1])) for i in range(0, len(flag), 2)])`
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Reversing/Transformation]
└─$ wget https://mercury.picoctf.net/static/e47483f88b12f2ab0c46315afc12f64d/enc
--2024-11-21 21:26:43--  https://mercury.picoctf.net/static/e47483f88b12f2ab0c46315afc12f64d/enc
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 57 [application/octet-stream]
Saving to: ‘enc’

enc                          100%[============================================>]      57  --.-KB/s    in 0s      

2024-11-21 21:26:44 (53.7 MB/s) - ‘enc’ saved [57/57]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/Transformation]
└─$ cat enc          
灩捯䍔䙻ㄶ形楴獟楮獴㌴摟潦弸彥ㄴㅡて㝽                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/Transformation]
└─$ nano solve.py  
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/Transformation]
└─$ cat solve.py
enc_flag = open("enc").read()
flag = ""

for i in range(0, len(enc_flag)):
        char1 = chr((ord(enc_flag[i]) >> 8))
        char2 = chr(enc_flag[i].encode('utf-16be')[-1])
        flag += char1
        flag += char2

print("Flag: " + flag)
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/Transformation]
└─$ python3 solve.py  
Flag: picoCTF{16_bits_inst34d_of_8_e141a0f7}
```

- ##### Luego de desencriptar el texto encriptado mediante un script de Python, obtenemos la bandera.
```
Flag: picoCTF{16_bits_inst34d_of_8_e141a0f7}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)