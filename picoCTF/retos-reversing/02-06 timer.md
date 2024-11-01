## Objetivo
You will find the flag after analysing this apk.
Download [here](https://artifacts.picoctf.net/c/449/timer.apk).
## Solución
```

┌──(kali㉿kali)-[~/picoCTF/Reversing/timer]
└─$ wget https://artifacts.picoctf.net/c/449/timer.apk       
--2024-10-30 12:38:07--  https://artifacts.picoctf.net/c/449/timer.apk
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.100, 3.161.55.26, 3.161.55.64, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.100|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4678467 (4.5M) [application/octet-stream]
Saving to: ‘timer.apk’

timer.apk                    100%[============================================>]   4.46M  3.44MB/s    in 1.3s    

2024-10-30 12:38:09 (3.44 MB/s) - ‘timer.apk’ saved [4678467/4678467]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/timer]
└─$ file timer.apk       
timer.apk: Android package (APK), with zipflinger virtual entry, with APK Signing Block
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/timer]
└─$ unzip timer.apk
Archive:  timer.apk
  inflating: META-INF/com/android/build/gradle/app-metadata.properties  
  inflating: classes3.dex            
  inflating: classes2.dex            
  inflating: AndroidManifest.xml     
  inflating: res/anim/abc_fade_in.xml
.   .   .
  inflating: kotlin/reflect/reflect.kotlin_builtins  
  inflating: classes.dex             
  inflating: META-INF/CERT.SF        
  inflating: META-INF/CERT.RSA       
  inflating: META-INF/MANIFEST.MF    
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/timer]
└─$ grep -R picoCTF                
grep: classes3.dex: binary file matches
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/timer]
└─$ find . -name classes3.dex
./classes3.dex
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/timer]
└─$ strings classes3.dex | grep picoCTF    
*picoCTF{t1m3r_r3v3rs3d_succ355fully_17496}
```

- ##### Después de descomprimir y buscar en qué archivo se encuentra la palabra clave, hacemos un strings a dicho archivo y obtenemos la bandera.
```
Flag: picoCTF{t1m3r_r3v3rs3d_succ355fully_17496}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)