## Objetivo
The password for the next level can be retrieved by submitting the password of the current level to **port 30001 on localhost** using SSL/TLS encryption.

**Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.**
## Datos de Acceso al Nivel
- **Puerto:** 2220
##### Se usará el usuario "bandit15":
- **Usuario:** bandit15
- **Contraseña:** 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
##### Después de conseguir la contraseña encriptada:
- **Usuario:** bandit16
- **Contraseña descubierta:** kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
## Solución
```
bandit15@bandit:~$ openssl s_client -connect localhost:30001
CONNECTED(00000003)
Can't use SSL_get_servername
depth=0 CN = SnakeOil
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = SnakeOil
verify return:1
---
Certificate chain
 0 s:CN = SnakeOil
   i:CN = SnakeOil
   a:PKEY: rsaEncryption, 4096 (bit); sigalg: RSA-SHA256
   v:NotBefore: Jun 10 03:59:50 2024 GMT; NotAfter: Jun  8 03:59:50 2034 GMT
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIFBzCCAu+gAwIBAgIUBLz7DBxA0IfojaL/WaJzE6Sbz7cwDQYJKoZIhvcNAQEL
BQAwEzERMA8GA1UEAwwIU25ha2VPaWwwHhcNMjQwNjEwMDM1OTUwWhcNMzQwNjA4
MDM1OTUwWjATMREwDwYDVQQDDAhTbmFrZU9pbDCCAiIwDQYJKoZIhvcNAQEBBQAD
ggIPADCCAgoCggIBANI+P5QXm9Bj21FIPsQqbqZRb5XmSZZJYaam7EIJ16Fxedf+
jXAv4d/FVqiEM4BuSNsNMeBMx2Gq0lAfN33h+RMTjRoMb8yBsZsC063MLfXCk4p+
09gtGP7BS6Iy5XdmfY/fPHvA3JDEScdlDDmd6Lsbdwhv93Q8M6POVO9sv4HuS4t/
jEjr+NhE+Bjr/wDbyg7GL71BP1WPZpQnRE4OzoSrt5+bZVLvODWUFwinB0fLaGRk
GmI0r5EUOUd7HpYyoIQbiNlePGfPpHRKnmdXTTEZEoxeWWAaM1VhPGqfrB/Pnca+
vAJX7iBOb3kHinmfVOScsG/YAUR94wSELeY+UlEWJaELVUntrJ5HeRDiTChiVQ++
wnnjNbepaW6shopybUF3XXfhIb4NvwLWpvoKFXVtcVjlOujF0snVvpE+MRT0wacy
tHtjZs7Ao7GYxDz6H8AdBLKJW67uQon37a4MI260ADFMS+2vEAbNSFP+f6ii5mrB
18cY64ZaF6oU8bjGK7BArDx56bRc3WFyuBIGWAFHEuB948BcshXY7baf5jjzPmgz
mq1zdRthQB31MOM2ii6vuTkheAvKfFf+llH4M9SnES4NSF2hj9NnHga9V08wfhYc
x0W6qu+S8HUdVF+V23yTvUNgz4Q+UoGs4sHSDEsIBFqNvInnpUmtNgcR2L5PAgMB
AAGjUzBRMB0GA1UdDgQWBBTPo8kfze4P9EgxNuyk7+xDGFtAYzAfBgNVHSMEGDAW
gBTPo8kfze4P9EgxNuyk7+xDGFtAYzAPBgNVHRMBAf8EBTADAQH/MA0GCSqGSIb3
DQEBCwUAA4ICAQAKHomtmcGqyiLnhziLe97Mq2+Sul5QgYVwfx/KYOXxv2T8ZmcR
Ae9XFhZT4jsAOUDK1OXx9aZgDGJHJLNEVTe9zWv1ONFfNxEBxQgP7hhmDBWdtj6d
taqEW/Jp06X+08BtnYK9NZsvDg2YRcvOHConeMjwvEL7tQK0m+GVyQfLYg6jnrhx
egH+abucTKxabFcWSE+Vk0uJYMqcbXvB4WNKz9vj4V5Hn7/DN4xIjFko+nREw6Oa
/AUFjNnO/FPjap+d68H1LdzMH3PSs+yjGid+6Zx9FCnt9qZydW13Miqg3nDnODXw
+Z682mQFjVlGPCA5ZOQbyMKY4tNazG2n8qy2famQT3+jF8Lb6a4NGbnpeWnLMkIu
jWLWIkA9MlbdNXuajiPNVyYIK9gdoBzbfaKwoOfSsLxEqlf8rio1GGcEV5Hlz5S2
txwI0xdW9MWeGWoiLbZSbRJH4TIBFFtoBG0LoEJi0C+UPwS8CDngJB4TyrZqEld3
rH87W+Et1t/Nepoc/Eoaux9PFp5VPXP+qwQGmhir/hv7OsgBhrkYuhkjxZ8+1uk7
tUWC/XM0mpLoxsq6vVl3AJaJe1ivdA9xLytsuG4iv02Juc593HXYR8yOpow0Eq2T
U5EyeuFg5RXYwAPi7ykw1PW7zAPL4MlonEVz+QXOSx6eyhimp1VZC11SCg==
-----END CERTIFICATE-----
subject=CN = SnakeOil
issuer=CN = SnakeOil
---
No client certificate CA names sent
Peer signing digest: SHA256
Peer signature type: RSA-PSS
Server Temp Key: X25519, 253 bits
---
SSL handshake has read 2103 bytes and written 373 bytes
Verification error: self-signed certificate
---
New, TLSv1.3, Cipher is TLS_AES_256_GCM_SHA384
Server public key is 4096 bit
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 18 (self-signed certificate)
---
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: A51814421335301FF13C1576FE8310B1B3BE9D23548AA15ACED3854307057F5A
    Session-ID-ctx:
    Resumption PSK: 0EB7005D6F3739727905552C14A9A9C5B215DD65CBEF4B1B477CE181DD45ED47F82DB939F5BADD3E2757EB228BD68E64
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
    0000 - 43 87 d0 c4 a5 49 95 26-c8 3e eb 08 d7 47 78 ca   C....I.&.>...Gx.
    0010 - 4a d0 d1 7d e5 31 83 da-9e 8e cb a3 bb 83 91 0a   J..}.1..........
    0020 - 96 c4 94 6a 8f a0 13 0d-ad a1 74 35 e0 07 97 f3   ...j......t5....
    0030 - 63 49 b6 7d 62 a1 2e 8c-8b af ba 53 24 b0 04 7e   cI.}b......S$..~
    0040 - 76 f5 2b 59 5f fc 10 3e-fa d2 81 32 24 3c 11 8b   v.+Y_..>...2$<..
    0050 - 43 4c 01 b5 a7 27 73 d3-95 bb cc 30 55 c2 bd 35   CL...'s....0U..5
    0060 - dd f0 77 1e 0b 62 43 a9-49 51 6f a3 f3 5c a2 f0   ..w..bC.IQo..\..
    0070 - 05 f0 93 1f 7f 3d a8 7c-4e 4d 8b 6e 10 5d ff 67   .....=.|NM.n.].g
    0080 - 74 e4 78 e1 f0 66 a1 a0-5f 22 da fc 15 c3 47 1d   t.x..f.._"....G.
    0090 - e5 5f 5e 90 24 ad aa a0-7a a9 97 af 13 72 07 4a   ._^.$...z....r.J
    00a0 - 58 74 9f cb 1e ec 6e 08-89 45 f3 42 29 f5 06 58   Xt....n..E.B)..X
    00b0 - a8 ed a1 aa 41 30 6d 02-b1 50 31 42 27 ab e5 46   ....A0m..P1B'..F
    00c0 - 67 dc 48 73 d0 27 e4 1c-c6 d4 27 fa 1f e7 c0 ea   g.Hs.'....'.....
    00d0 - 3c 78 b9 1b d4 ed 78 a1-d2 47 86 68 08 43 8f 5d   <x....x..G.h.C.]

    Start Time: 1724992521
    Timeout   : 7200 (sec)
    Verify return code: 18 (self-signed certificate)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: 95B7618FE9EF01B5D1F556C714F0F93FF00F95D2A49A195F0BC1011F9E800BB7
    Session-ID-ctx:
    Resumption PSK: 51F5E746BD6C7D62F283A5D0ED2E6811F1755149605068BB0C5D602CAA6F723C2B76163BC0C1D9517AC9EA3F43F7DB29
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
    0000 - 43 87 d0 c4 a5 49 95 26-c8 3e eb 08 d7 47 78 ca   C....I.&.>...Gx.
    0010 - 95 58 09 f6 2a 11 cf 06-8b c2 3b 9e a5 db 91 b6   .X..*.....;.....
    0020 - e4 b6 fe a5 6b 11 8c 71-c5 e2 7c 03 f8 9a e2 d0   ....k..q..|.....
    0030 - c1 4d 9a 8d 9c 6a a6 45-43 cc 10 52 26 df 35 1c   .M...j.EC..R&.5.
    0040 - 7b be fe 68 45 d5 b0 e2-3f 49 87 24 73 8e 4e 56   {..hE...?I.$s.NV
    0050 - c7 63 b3 7e 01 6f d7 eb-3f 58 3c a2 d6 b7 a7 98   .c.~.o..?X<.....
    0060 - 2a db 35 4e 9d 6c 8f 7a-4b fc 27 1f b4 53 f0 6c   *.5N.l.zK.'..S.l
    0070 - 51 cb c7 f8 d7 b0 b5 15-24 e9 5f 41 f8 a1 23 7c   Q.......$._A..#|
    0080 - 6b b4 9c 4f de fb 37 a9-65 56 14 e0 22 e3 90 40   k..O..7.eV.."..@
    0090 - df d7 49 24 a7 75 46 cd-9e 86 b2 5d 32 a0 af af   ..I$.uF....]2...
    00a0 - 32 1c bd aa 99 04 cb 65-67 77 97 1a 89 9f 94 fe   2......egw......
    00b0 - ce e2 4d 7e 4a 8b 66 50-d1 47 b6 ce e0 79 0f c5   ..M~J.fP.G...y..
    00c0 - 0b af 30 40 cc e0 d0 93-94 23 59 d3 27 17 da 07   ..0@.....#Y.'...
    00d0 - 5f 8a d9 97 c0 17 b8 a7-e3 39 a7 15 e8 bf 21 4e   _........9....!N

    Start Time: 1724992521
    Timeout   : 7200 (sec)
    Verify return code: 18 (self-signed certificate)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
Correct!
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx

closed
```

- ##### Cierre de sesión del usuario "bandit15".
```
bandit15@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.
```
## Notas Adicionales
- **openssl s_client -connect localhost:30001** - **penssl**: Es el comando principal de OpenSSL, una herramienta de línea de comandos que se utiliza para diversas operaciones relacionadas con criptografía y SSL/TLS.
- **s_client**: Especifica que queremos utilizar la funcionalidad de cliente SSL/TLS de OpenSSL.
- **-connect localhost:30001**: Esta opción indica a qué servidor y puerto se debe conectar OpenSSL. En este caso, se está conectando al servidor que se ejecuta en la misma máquina (localhost) en el puerto 30001.
## Referencias
- [OverTheWire](https://overthewire.org/wargames/bandit/bandit1.html)
- [OpenSSL](https://es.wikipedia.org/wiki/OpenSSL)