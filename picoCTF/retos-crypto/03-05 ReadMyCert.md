## Objetivo
How about we take you on an adventure on exploring certificate signing requests Take a look at this CSR file [here](https://artifacts.picoctf.net/c/426/readmycert.csr).
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Crypto/ReadMyCert]
└─$ wget https://artifacts.picoctf.net/c/426/readmycert.csr
--2024-10-23 13:49:12--  https://artifacts.picoctf.net/c/426/readmycert.csr
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.100, 3.161.55.64, 3.161.55.61, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.100|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 997 [application/octet-stream]
Saving to: ‘readmycert.csr’

readmycert.csr               100%[============================================>]     997  --.-KB/s    in 0.03s   

2024-10-23 13:49:13 (35.7 KB/s) - ‘readmycert.csr’ saved [997/997]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/ReadMyCert]
└─$ cat readmycert.csr
-----BEGIN CERTIFICATE REQUEST-----
MIICpzCCAY8CAQAwPDEmMCQGA1UEAwwdcGljb0NURntyZWFkX215Y2VydF80MWQx
Yzc0Y30xEjAQBgNVBCkMCWN0ZlBsYXllcjCCASIwDQYJKoZIhvcNAQEBBQADggEP
ADCCAQoCggEBAOdcDj2/m1LxBrXb3ch9+2BtKd3b8NFn4USXA5JORPfeGcDdIX4V
SiRkFrbxLOit6SZwoAyWQ7SmWJTtzADbr82qTbVktGJj9YebwK57jpMEL6BPT9YA
cE9AGFtVJycL+IXqtlTqAGq4DjcPtAs5THgIPDJ+aTgRDHP8YItfEFs+aywLd8kS
WSmttEjS874Tc++b9PbQ246IIrtQ701/I1NB0S/inzQvPCui+hLSHgMFkGS4leN7
7xJORGAQueRejKuYnOs6HbAlbK0oIWKR83BxkntDBee8KhOPDynHDgYoblERl8rL
JAfcVogKNSniIztMkzh408V9mbLHOfsr6eUCAwEAAaAmMCQGCSqGSIb3DQEJDjEX
MBUwEwYDVR0lBAwwCgYIKwYBBQUHAwIwDQYJKoZIhvcNAQELBQADggEBAFEyhXpa
nZz/ofFW/31ryCF3nyvNg9pOyIniu8kcpiteSaOkNm4YREBCRwj92X3Wy1MUi/7Z
urXwR1TcRTxLdPqeVBn4nsJclAgZqMKcT0ftz5fAM/Xg5whwBHEBb1qFVN+HGhPo
1TKfhXunICyrjNWvM+2fudM2RPsGb0sBsjLAe1/6OJK82LJBoHQ0GlCPDN1tncrl
lpzHACCFPv7LMVF9BSkZDCQNglU1NYDDelXZezfXLbio/a1RC2k4rs+jorVmFese
elZFzORDsCzlgD87NvBUMZWI8J5+9fZeaWAQQfhwEiZOVn8IcjLUxUraxt4rbI/h
0EUJJuCjGyTjRpQ=
-----END CERTIFICATE REQUEST-----
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/ReadMyCert]
└─$ openssl req -in readmycert.csr -text                                                
Certificate Request:
    Data:
        Version: 1 (0x0)
        Subject: CN=picoCTF{read_mycert_41d1c74c}, name=ctfPlayer
        Subject Public Key Info:
            Public Key Algorithm: rsaEncryption
                Public-Key: (2048 bit)
                Modulus:
                    00:e7:5c:0e:3d:bf:9b:52:f1:06:b5:db:dd:c8:7d:
                    fb:60:6d:29:dd:db:f0:d1:67:e1:44:97:03:92:4e:
                    44:f7:de:19:c0:dd:21:7e:15:4a:24:64:16:b6:f1:
                    2c:e8:ad:e9:26:70:a0:0c:96:43:b4:a6:58:94:ed:
                    cc:00:db:af:cd:aa:4d:b5:64:b4:62:63:f5:87:9b:
                    c0:ae:7b:8e:93:04:2f:a0:4f:4f:d6:00:70:4f:40:
                    18:5b:55:27:27:0b:f8:85:ea:b6:54:ea:00:6a:b8:
                    0e:37:0f:b4:0b:39:4c:78:08:3c:32:7e:69:38:11:
                    0c:73:fc:60:8b:5f:10:5b:3e:6b:2c:0b:77:c9:12:
                    59:29:ad:b4:48:d2:f3:be:13:73:ef:9b:f4:f6:d0:
                    db:8e:88:22:bb:50:ef:4d:7f:23:53:41:d1:2f:e2:
                    9f:34:2f:3c:2b:a2:fa:12:d2:1e:03:05:90:64:b8:
                    95:e3:7b:ef:12:4e:44:60:10:b9:e4:5e:8c:ab:98:
                    9c:eb:3a:1d:b0:25:6c:ad:28:21:62:91:f3:70:71:
                    92:7b:43:05:e7:bc:2a:13:8f:0f:29:c7:0e:06:28:
                    6e:51:11:97:ca:cb:24:07:dc:56:88:0a:35:29:e2:
                    23:3b:4c:93:38:78:d3:c5:7d:99:b2:c7:39:fb:2b:
                    e9:e5
                Exponent: 65537 (0x10001)
        Attributes:
            Requested Extensions:
                X509v3 Extended Key Usage: 
                    TLS Web Client Authentication
    Signature Algorithm: sha256WithRSAEncryption
    Signature Value:
        51:32:85:7a:5a:9d:9c:ff:a1:f1:56:ff:7d:6b:c8:21:77:9f:
        2b:cd:83:da:4e:c8:89:e2:bb:c9:1c:a6:2b:5e:49:a3:a4:36:
        6e:18:44:40:42:47:08:fd:d9:7d:d6:cb:53:14:8b:fe:d9:ba:
        b5:f0:47:54:dc:45:3c:4b:74:fa:9e:54:19:f8:9e:c2:5c:94:
        08:19:a8:c2:9c:4f:47:ed:cf:97:c0:33:f5:e0:e7:08:70:04:
        71:01:6f:5a:85:54:df:87:1a:13:e8:d5:32:9f:85:7b:a7:20:
        2c:ab:8c:d5:af:33:ed:9f:b9:d3:36:44:fb:06:6f:4b:01:b2:
        32:c0:7b:5f:fa:38:92:bc:d8:b2:41:a0:74:34:1a:50:8f:0c:
        dd:6d:9d:ca:e5:96:9c:c7:00:20:85:3e:fe:cb:31:51:7d:05:
        29:19:0c:24:0d:82:55:35:35:80:c3:7a:55:d9:7b:37:d7:2d:
        b8:a8:fd:ad:51:0b:69:38:ae:cf:a3:a2:b5:66:15:eb:1e:7a:
        56:45:cc:e4:43:b0:2c:e5:80:3f:3b:36:f0:54:31:95:88:f0:
        9e:7e:f5:f6:5e:69:60:10:41:f8:70:12:26:4e:56:7f:08:72:
        32:d4:c5:4a:da:c6:de:2b:6c:8f:e1:d0:45:09:26:e0:a3:1b:
        24:e3:46:94
-----BEGIN CERTIFICATE REQUEST-----
MIICpzCCAY8CAQAwPDEmMCQGA1UEAwwdcGljb0NURntyZWFkX215Y2VydF80MWQx
Yzc0Y30xEjAQBgNVBCkMCWN0ZlBsYXllcjCCASIwDQYJKoZIhvcNAQEBBQADggEP
ADCCAQoCggEBAOdcDj2/m1LxBrXb3ch9+2BtKd3b8NFn4USXA5JORPfeGcDdIX4V
SiRkFrbxLOit6SZwoAyWQ7SmWJTtzADbr82qTbVktGJj9YebwK57jpMEL6BPT9YA
cE9AGFtVJycL+IXqtlTqAGq4DjcPtAs5THgIPDJ+aTgRDHP8YItfEFs+aywLd8kS
WSmttEjS874Tc++b9PbQ246IIrtQ701/I1NB0S/inzQvPCui+hLSHgMFkGS4leN7
7xJORGAQueRejKuYnOs6HbAlbK0oIWKR83BxkntDBee8KhOPDynHDgYoblERl8rL
JAfcVogKNSniIztMkzh408V9mbLHOfsr6eUCAwEAAaAmMCQGCSqGSIb3DQEJDjEX
MBUwEwYDVR0lBAwwCgYIKwYBBQUHAwIwDQYJKoZIhvcNAQELBQADggEBAFEyhXpa
nZz/ofFW/31ryCF3nyvNg9pOyIniu8kcpiteSaOkNm4YREBCRwj92X3Wy1MUi/7Z
urXwR1TcRTxLdPqeVBn4nsJclAgZqMKcT0ftz5fAM/Xg5whwBHEBb1qFVN+HGhPo
1TKfhXunICyrjNWvM+2fudM2RPsGb0sBsjLAe1/6OJK82LJBoHQ0GlCPDN1tncrl
lpzHACCFPv7LMVF9BSkZDCQNglU1NYDDelXZezfXLbio/a1RC2k4rs+jorVmFese
elZFzORDsCzlgD87NvBUMZWI8J5+9fZeaWAQQfhwEiZOVn8IcjLUxUraxt4rbI/h
0EUJJuCjGyTjRpQ=
-----END CERTIFICATE REQUEST-----
```

- ##### Después de obtener el certificado, tenemos la bandera.
```
Flag: picoCTF{read_mycert_41d1c74c}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)