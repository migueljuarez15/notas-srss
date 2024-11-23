## Objetivo
Oracles can be your best friend, they will decrypt anything, except the flag's ciphertext. How will you break it? Connect with `nc mercury.picoctf.net 42248`.
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Crypto/NoPaddingNoProblem]
└─$ nc mercury.picoctf.net 42248
Welcome to the Padding Oracle Challenge
This oracle will take anything you give it and decrypt using RSA. It will not accept the ciphertext with the secret message... Good Luck!


n: 90029158937952709218479922111627594040318378157895262309468978200792252423553796124201719620356579669687733828482152338235604711121788486616712590828557607844837979351531095725079763772700917160718888718885377390433896067460631646222128689068925845937089962426080545008065798619757821356516339510599324117079
e: 65537
ciphertext: 77528453905315868794059730265683211154612726785301035607710833199422761132466364041262912544231766847255890923048997828234601357882759866415171184881729069930582200935865579904095865547388338521044674220305889306021034439223411040464955565678463782256328713954311338539067270921555605367554838398689435300822


Give me ciphertext to decrypt: 77528453905315868794059730265683211154612726785301035607710833199422761132466364041262912544231766847255890923048997828234601357882759866415171184881729069930582200935865579904095865547388338521044674220305889306021034439223411040464955565678463782256328713954311338539067270921555605367554838398689435300822
Will not decrypt the ciphertext. Try Again
Give me ciphertext to decrypt: ^C
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/NoPaddingNoProblem]
└─$ nano solve.py               
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/NoPaddingNoProblem]
└─$ python3 solve.py
[*] Checking for new versions of pwntools
    To disable this functionality, set the contents of /home/kali/.cache/.pwntools-cache-3.11/update to 'never' (old way).
    Or add the following lines to ~/.pwn.conf or /home/kali/.config/pwn.conf (or /etc/pwn.conf system-wide):
        [update]
        interval=never
[*] You have the latest version of Pwntools (4.13.1)
[+] Opening connection to mercury.picoctf.net on port 42248: Done
/home/kali/picoCTF/Crypto/NoPaddingNoProblem/solve.py:17: BytesWarning: Text is not bytes; assuming ASCII, no guarantees. See https://docs.pwntools.com/#bytes
  r.sendlineafter(b'Give me ciphertext to decrypt: ', str(payload))
Doubled Plain: 580550060391700078946913236734911770139931497702556153513487440893406629034802718534645538074938502890769716268793877259514
Plain Text Hex: 7069636f4354467b6d347962335f54683073655f6d337335346733735f3472335f646966757272656e745f373431363032327d
Plain Text: picoCTF{m4yb3_Th0se_m3s54g3s_4r3_difurrent_7416022}
[*] Closed connection to mercury.picoctf.net port 42248
```

- ##### Después de ejecutar el script de Python, obtenemos la bandera.
```
Flag: picoCTF{m4yb3_Th0se_m3s54g3s_4r3_difurrent_7416022}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)