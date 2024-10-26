## Objetivo
Can you find the flag? [shark2.pcapng](https://mercury.picoctf.net/static/75300327ce3b9f252e9b8911997c8b0a/shark2.pcapng).
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Forensics/WiresharkTwooTwoooTwoTwoo]
└─$ wget https://mercury.picoctf.net/static/75300327ce3b9f252e9b8911997c8b0a/shark2.pcapng
--2024-10-26 04:22:34--  https://mercury.picoctf.net/static/75300327ce3b9f252e9b8911997c8b0a/shark2.pcapng
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3520112 (3.4M) [application/octet-stream]
Saving to: ‘shark2.pcapng’

shark2.pcapng                100%[============================================>]   3.36M  3.99MB/s    in 0.8s    

2024-10-26 04:22:36 (3.99 MB/s) - ‘shark2.pcapng’ saved [3520112/3520112]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/WiresharkTwooTwoooTwoTwoo]
└─$ file shark2.pcapng     
shark2.pcapng: pcapng capture file - version 1.0
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/WiresharkTwooTwoooTwoTwoo]
└─$ strings shark2.pcapng | grep picoCTF 
picoCTF{bfe48e8500c454d647c55a4471985e776a07b26cba64526713f43758599aa98b}
picoCTF{bda69bdf8f570a9aaab0e4108a0fa5f64cb26ba7d2269bb63f68af5d98b98245}
picoCTF{fe83bcb6cfd43d3b79392f6a4232685f6ed4e7a789c2ce559cf3c1ab6adbe34b}
.   .   .
picoCTF{7282e048d6d32383b65f3a03b1101219ac73f7f538446b78d1b2b334e0985447}
picoCTF{98406c4acbf0f57b3ccbc923aab5a603d70f86d507f422d9bd8656398f53433e}
picoCTF{3fe0b2788f30d9cb9f77d3b2752f13c554fe7f0e7a2883e57c8a44b34f35675c}

┌──(kali㉿kali)-[~/picoCTF/Forensics/WiresharkTwooTwoooTwoTwoo]
└─$ wireshark shark2.pcapng
```

- ##### Inspeccionando los paquetes UDP, hay caracteres que pueden ser desencriptados en base64, por lo que eso se hará.
```
┌──(kali㉿kali)-[~/picoCTF/Forensics/WiresharkTwooTwoooTwoTwoo]
└─$ echo cGljb0NURntkbnNfM3hmMWxfZnR3X2RlYWRiZWVmfQ== | base64 -d                      
picoCTF{dns_3xf1l_ftw_deadbeef}
```

- ##### Una vez desencriptado ese texto, obtenemos la bandera.
```
Flag: picoCTF{dns_3xf1l_ftw_deadbeef}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)