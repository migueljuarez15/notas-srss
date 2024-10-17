## Objetivo
We made a lot of substitutions to encrypt this. Can you decrypt it? Connect with `nc jupiter.challenges.picoctf.org 39894`.
## Solución
- ##### Al conectarnos al netcat, podemos ver que nos dan un texto completamente encriptado, usaremos el algoritmo de Sustitución para desencriptarlo.
```
┌──(kali㉿kali)-[~/picoCTF/Crypto/WavesOverLambda]
└─$ nc jupiter.challenges.picoctf.org 39894        
-------------------------------------------------------------------------------
qdxokeja fpkp la udck mieo - mkptcpxqu_la_q_dzpk_iehgye_eomiqojucp
-------------------------------------------------------------------------------
gpjsppx ca jfpkp sea, ea l fezp eikpeyu aely adhpsfpkp, jfp gdxy dm jfp ape. gpalypa fdiylxo dck fpekja jdopjfpk jfkdcof idxo npkldya dm apnekejldx, lj fey jfp pmmpqj dm hevlxo ca jdipkexj dm peqf djfpk'a uekxaexy pzpx qdxzlqjldxa. jfp iesupkjfp gpaj dm diy mpiidsafey, gpqecap dm fla hexu upeka exy hexu zlkjcpa, jfp dxiu qcafldx dx ypqv, exy sea iulxo dx jfp dxiu kco. jfp eqqdcxjexj fey gkdcofj dcj eikpeyu e gdb dm ydhlxdpa, exy sea jdulxo ekqfljpqjckeiiu sljf jfp gdxpa. hekids aej qkdaa-ipoopy klofj emj, ipexlxo eoelxaj jfp hlrrpx-heaj. fp fey acxvpx qfppva, e upiids qdhnipbldx, e ajkelofj geqv, ex eaqpjlq eanpqj, exy, sljf fla ekha ykdnnpy, jfp neiha dm fexya dcjsekya, kpaphgipy ex lydi. jfp ylkpqjdk, aejlamlpy jfp exqfdk fey oddy fdiy, heyp fla seu emj exy aej ydsx ehdxoaj ca. sp pbqfexopy e mps sdkya ierliu. emjpksekya jfpkp sea alipxqp dx gdeky jfp ueqfj. mdk adhp kpeadx dk djfpk sp yly xdj gpolx jfej oehp dm ydhlxdpa. sp mpij hpyljejlzp, exy mlj mdk xdjflxo gcj nieqly ajeklxo. jfp yeu sea pxylxo lx e apkpxlju dm ajlii exy pbtclaljp gkliilexqp. jfp sejpk afdxp neqlmlqeiiu; jfp avu, sljfdcj e anpqv, sea e gpxlox lhhpxalju dm cxajelxpy ilofj; jfp zpku hlaj dx jfp paapb hekaf sea ilvp e oecru exy keylexj megklq, fcxo mkdh jfp sddypy klapa lxiexy, exy ykenlxo jfp ids afdkpa lx ylenfexdca mdiya. dxiu jfp oiddh jd jfp spaj, gkddylxo dzpk jfp cnnpk kpeqfpa, gpqehp hdkp adhgkp pzpku hlxcjp, ea lm exopkpy gu jfp ennkdeqf dm jfp acx.
```

- ##### Se desencripta el texto mediante una sustitución, donde se usó lo siguiente:
```
KEY: sxuoahbmltrifpgeczwqykjndv

TEXTO DESENCRIPTADO:
-------------------------------------------------------------------------------
congrats here is your flag - frequency_is_c_over_lambda_agflcgtyue
-------------------------------------------------------------------------------
between us there was, as i have already said somewhere, the bond of the sea. besides holding our hearts together through long periods of separation, it had the effect of making us tolerant of each other's yarnsand even convictions. the lawyerthe best of old fellowshad, because of his many years and many virtues, the only cushion on deck, and was lying on the only rug. the accountant had brought out already a box of dominoes, and was toying architecturally with the bones. marlow sat cross-legged right aft, leaning against the mizzen-mast. he had sunken cheeks, a yellow complexion, a straight back, an ascetic aspect, and, with his arms dropped, the palms of hands outwards, resembled an idol. the director, satisfied the anchor had good hold, made his way aft and sat down amongst us. we exchanged a few words lazily. afterwards there was silence on board the yacht. for some reason or other we did not begin that game of dominoes. we felt meditative, and fit for nothing but placid staring. the day was ending in a serenity of still and exquisite brilliance. the water shone pacifically; the sky, without a speck, was a benign immensity of unstained light; the very mist on the essex marsh was like a gauzy and radiant fabric, hung from the wooded rises inland, and draping the low shores in diaphanous folds. only the gloom to the west, brooding over the upper reaches, became more sombre every minute, as if angered by the approach of the sun.
```

- ##### Una vez desencriptado el texto, obtenemos la bandera, aunque viene en un formato al que no estamos acostumbrados.
```
Flag: frequency_is_c_over_lambda_agflcgtyue
```
## Notas Adicionales
- En criptografía, el **cifrado por sustitución** es un método de cifrado por el que unidades de texto plano son sustituidas con texto cifrado siguiendo un sistema regular; las "unidades" pueden ser una sola letra (el caso más común), pares de letras, tríos de letras, mezclas de lo anterior, entre otros. El receptor descifra el texto realizando la sustitución inversa. 
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)
- [SubstitutionSolver](https://www.guballa.de/substitution-solver)