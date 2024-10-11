## Objetivo
I've hidden a flag in this file. Can you find it? [Forensics is fun.pptm](https://mercury.picoctf.net/static/c00c449c3b08daaccacca6f9d5c55d49/Forensics is fun.pptm)
## Solución
- ##### Descargamos el archivo, y podemos observar que es un archivo que pretende ser una presentación de PowerPoint. Lo descomprimiremos y podemos ver que se generaron diferentes archivos/directorios
```
┌──(kali㉿kali)-[~/picoCTF/MacroHardWeakEdge]
└─$ wget https://mercury.picoctf.net/static/c00c449c3b08daaccacca6f9d5c55d49/Forensics%20is%20fun.pptm
--2024-10-10 17:43:22--  https://mercury.picoctf.net/static/c00c449c3b08daaccacca6f9d5c55d49/Forensics%20is%20fun.pptm
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 100093 (98K) [application/octet-stream]
Saving to: ‘Forensics is fun.pptm’

Forensics is fun.pptm        100%[============================================>]  97.75K  --.-KB/s    in 0.1s    

2024-10-10 17:43:23 (687 KB/s) - ‘Forensics is fun.pptm’ saved [100093/100093]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/MacroHardWeakEdge]
└─$ file "Forensics is fun.pptm"
Forensics is fun.pptm: Microsoft PowerPoint 2007+
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/MacroHardWeakEdge]
└─$ unzip "Forensics is fun.pptm"
Archive:  Forensics is fun.pptm
  inflating: [Content_Types].xml     
  inflating: _rels/.rels             
  inflating: ppt/presentation.xml    
  inflating: ppt/slides/_rels/slide46.xml.rels  
  inflating: ppt/slides/slide1.xml   
  .   .   .
  inflating: ppt/tableStyles.xml     
  inflating: docProps/core.xml       
  inflating: docProps/app.xml        
  inflating: ppt/slideMasters/hidden  
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/MacroHardWeakEdge]
└─$ ls
'[Content_Types].xml'   docProps  'Forensics is fun.pptm'   ppt   _rels
```

- ##### Abriremos Visual Studio Code mediante la terminal en la misma carpeta del reto, y al buscar en el directorio "ppt/_rels/slideMasters" encontramos un archivo de texto "hidden", el cual contiene una cadena de texto encriptada en "base64", por lo que la decodificaremos.
```
┌──(kali㉿kali)-[~/picoCTF/MacroHardWeakEdge]
└─$ code .
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/MacroHardWeakEdge]
└─$ echo "Z m x h Z z o g c G l j b 0 N U R n t E M W R f d V 9 r b j B 3 X 3 B w d H N f c l 9 6 M X A 1 f Q" | tr -d " "
ZmxhZzogcGljb0NURntEMWRfdV9rbjB3X3BwdHNfcl96MXA1fQ
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/MacroHardWeakEdge]
└─$ echo "Z m x h Z z o g c G l j b 0 N U R n t E M W R f d V 9 r b j B 3 X 3 B w d H N f c l 9 6 M X A 1 f Q" | tr -d " " | base64 -d
flag: picoCTF{D1d_u_kn0w_ppts_r_z1p5}base64: invalid input
```

- ##### Una vez decodificada la cadena de texto, obtenemos la bandera.
```
Flag: picoCTF{D1d_u_kn0w_ppts_r_z1p5}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)