## Objetivo
Can you find the flag in [file](https://jupiter.challenges.picoctf.org/static/515f19f3612bfd97cd3f0c0ba32bd864/file)? This would be really tedious to look through manually, something tells me there is a better way.
## Solución
```
mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ wget https://jupiter.challenges.picoctf.org/static/515f19f3612bfd97cd3f0c0ba32bd864/file
--2024-09-16 23:44:20--  https://jupiter.challenges.picoctf.org/static/515f19f3612bfd97cd3f0c0ba32bd864/file
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 14551 (14K) [application/octet-stream]
Saving to: ‘file’

file                          100%[=================================================>]  14.21K  --.-KB/s    in 0s

2024-09-16 23:44:21 (27.9 MB/s) - ‘file’ saved [14551/14551]

mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ cat file
VbeB1PFG/-c3CqSCDZ*0vw%hB>Ql252>(tXWjyPLng6BFH  yO0ME|lAM^B 8_j&.7@+:NRQ4 Gwk4V?6_C*#vlk/YNVZdgV+q)(y!^M9 H*>x1uP-wKV-vEHkE*>L@u:.pOg:|LX1:&xe*AZEDhN$_A..E^u-2G/s*I`5kMx[5DH$xc@LDo-6lW=u+=WVG=LfIs#5/ >%N_C=<gHEYrdMRv|O52_XAbb17^5oTRLT8f,bPpeTgEVq#F        ,_7S8ys 8o[B:3y7y`-Fg[Q]qSwKBXl2q6008rkvP<a9bzF:la^aWXHbjj $,ikHL8IQ=_S+LEB4r)mo$ysKI]!?N|kL3KLjz!1GEH.i]X|e<;P,5M1nd08&JMF5VZ:*bd:!G73<,~      n~dYA&y9k6h     Ky2yE&HwvIN24.^5nH*m`J>frW)vd|s+S,j^Jxk1_S3>c&3K*2+]4dTLq^A.4RTdyZ>m! CF[9&h7#-u)ZLUWWaQ=W(2TRHs)leLBwd)#P<utKW
.   .   .
)CElyv,-9%vFJ]n$sNH5-ARysw#3xRe- .!Qt%*.|Nx]3Sn&e7h@=]d[t9 (z(Xy^[g]JJRt.0E?#Wt=h)X2sGy3^NTeD#%:8TnFPoo]8$Qr]+,X8oEuddl7O@-Qyr)A&[5i*?~z=~@k0[TYN4^#nyfE(#lHNQYUNg]ZsroF1:ZSj3rw&<.ogyfh5lMdg/fOL-NDwFaKVwFddMXC|DP3vXC7*!7u9DBWj2+tZuX5uT5GU#!C&ubs>dp1~4gz2mi?zH n$Ojv[X*9c];e!^Bh,)+8!Yy%b>(mlk6],h2(>T0B<I#U+5E#Wxg0Su`o~419i)c?oznRuI7PaNt^fE!Mo6fX9Zm^-CB7FyvB/a;/>_R;F1

mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ cat file | grep -r "picoCTF"
file:picoCTF{grep_is_good_to_find_things_5af9d829}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)