## Objetivo
Matryoshka dolls are a set of wooden dolls of decreasing size placed one inside another. What's the final one? Image: [this](https://mercury.picoctf.net/static/1b70cffdd2f05427fff97d13c496963f/dolls.jpg)
## Solución
- ##### Descargamos el archivo y podemos observar que es una imagen de una muñeca Matryoshka, la cual en sus "strings" podemos observar que puede ser descomprimida, por lo que descomprimiremos la imagen. Y al extraer la imagen, cambiaremos al directorio "base_images" múltiples veces que sea necesario.
```
┌──(kali㉿kali)-[~/picoCTF/MatryoshkaDoll]
└─$ wget https://mercury.picoctf.net/static/1b70cffdd2f05427fff97d13c496963f/dolls.jpg                
--2024-10-10 22:36:13--  https://mercury.picoctf.net/static/1b70cffdd2f05427fff97d13c496963f/dolls.jpg
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 651634 (636K) [application/octet-stream]
Saving to: ‘dolls.jpg’

dolls.jpg                    100%[============================================>] 636.36K  1.51MB/s    in 0.4s    

2024-10-10 22:36:14 (1.51 MB/s) - ‘dolls.jpg’ saved [651634/651634]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/MatryoshkaDoll]
└─$ exiftool dolls.jpg   
ExifTool Version Number         : 12.76
File Name                       : dolls.jpg
Directory                       : .
File Size                       : 652 kB
File Modification Date/Time     : 2021:03:15 20:23:04-04:00
File Access Date/Time           : 2024:10:10 22:36:14-04:00
File Inode Change Date/Time     : 2024:10:10 22:36:14-04:00
.   .   .
Pixel Units                     : meters
XMP Toolkit                     : XMP Core 5.4.0
Apple Data Offsets              : (Binary data 28 bytes, use -b option to extract)
Warning                         : [minor] Trailer data after PNG IEND chunk
Image Size                      : 594x1104
Megapixels                      : 0.656
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/MatryoshkaDoll]
└─$ strings -n 10 dolls.jpg                      
eiCCPICC Profile
Screenshot
iTXtXML:com.adobe.xmp
<x:xmpmeta xmlns:x="adobe:ns:meta/" x:xmptk="XMP Core 5.4.0">
   <rdf:RDF xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#">
      <rdf:Description rdf:about=""
            xmlns:exif="http://ns.adobe.com/exif/1.0/">
         <exif:PixelXDimension>594</exif:PixelXDimension>
         <exif:UserComment>Screenshot</exif:UserComment>
         <exif:PixelYDimension>1104</exif:PixelYDimension>
      </rdf:Description>
   </rdf:RDF>
</x:xmpmeta>
IDEEb^*Qcb4
Z9vT?vA/_$
a#;s;[gyjD
n3zY[>GAD
=,e< =*?Yp
3Sn'&bbGf'
\sMKn$R`eG
~wkwwG;~A
base_images/2_c.jpgUT
C}-Zjvj"""Z
/\6c7l*18Mj
Hr~&    8Ja7i,
t+Vp`B2AYq
se\45~|_4Z
%(oQ1y~?e?
Db^!u"tE=O
9)IZ9Rj|Fn
|YrAkJI_S,
cG3CKkcs3G
=T*N+b_Io8
-8(Ly<7-"`
kT_S0/,0L3
mlKszlh<f$
>,\vxk~[        .R
l_(ZU2&?IX
>KO<K-j3|sD
base_images/2_c.jpgUT
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/MatryoshkaDoll]
└─$ unzip dolls.jpg              
Archive:  dolls.jpg
warning [dolls.jpg]:  272492 extra bytes at beginning or within zipfile
  (attempting to process anyway)
  inflating: base_images/2_c.jpg     
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/MatryoshkaDoll]
└─$ ls
base_images  dolls.jpg
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/MatryoshkaDoll]
└─$ cd base_images   
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/MatryoshkaDoll/base_images]
└─$ ls
2_c.jpg
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/MatryoshkaDoll/base_images]
└─$ unzip 2_c.jpg
Archive:  2_c.jpg
warning [2_c.jpg]:  187707 extra bytes at beginning or within zipfile
  (attempting to process anyway)
  inflating: base_images/3_c.jpg     
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/MatryoshkaDoll/base_images]
└─$ cd base_images
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/MatryoshkaDoll/base_images/base_images]
└─$ ls
3_c.jpg
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/MatryoshkaDoll/base_images/base_images]
└─$ unzip 3_c.jpg
Archive:  3_c.jpg
warning [3_c.jpg]:  123606 extra bytes at beginning or within zipfile
  (attempting to process anyway)
  inflating: base_images/4_c.jpg     
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/MatryoshkaDoll/base_images/base_images]
└─$ cd base_images
                                                                                                                  
┌──(kali㉿kali)-[~/…/MatryoshkaDoll/base_images/base_images/base_images]
└─$ ls
4_c.jpg
                                                                                                                  
┌──(kali㉿kali)-[~/…/MatryoshkaDoll/base_images/base_images/base_images]
└─$ unzip 4_c.jpg
Archive:  4_c.jpg
warning [4_c.jpg]:  79578 extra bytes at beginning or within zipfile
  (attempting to process anyway)
  inflating: flag.txt                
                                                                                                                  
┌──(kali㉿kali)-[~/…/MatryoshkaDoll/base_images/base_images/base_images]
└─$ ls
4_c.jpg  flag.txt
                                                                                                                  
┌──(kali㉿kali)-[~/…/MatryoshkaDoll/base_images/base_images/base_images]
└─$ cat flag.txt      
picoCTF{bf6acf878dcbd752f4721e41b1b1b66b}
```

- ##### Una vez que llegamos a la imagen "4_c.jpg", al descomprimirla obtenemos el archivo "flag.txt", y obtenemos la bandera.
```
Flag: picoCTF{bf6acf878dcbd752f4721e41b1b1b66b}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)