## Objetivo
Find the flag in this [picture](https://jupiter.challenges.picoctf.org/static/916b07b4c87062c165ace1d3d31ef655/pico_img.png).
## Solución
- ##### Descargando el archivo que se nos da, podemos observar que es una imagen ".png". Usaremos la instrucción "exiftool" para ver los metadatos de la imagen.
```
┌──(kali㉿kali)-[~/picoCTF/SoMeta]
└─$ wget https://jupiter.challenges.picoctf.org/static/916b07b4c87062c165ace1d3d31ef655/pico_img.png
--2024-10-03 04:58:34--  https://jupiter.challenges.picoctf.org/static/916b07b4c87062c165ace1d3d31ef655/pico_img.png
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 108795 (106K) [application/octet-stream]
Saving to: ‘pico_img.png’

pico_img.png                 100%[============================================>] 106.25K  --.-KB/s    in 0.1s    

2024-10-03 04:58:35 (875 KB/s) - ‘pico_img.png’ saved [108795/108795]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/SoMeta]
└─$ ls                     
pico_img.png
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/SoMeta]
└─$ exiftool pico_img.png
ExifTool Version Number         : 12.76
File Name                       : pico_img.png
Directory                       : .
File Size                       : 109 kB
File Modification Date/Time     : 2020:10:26 14:38:23-04:00
File Access Date/Time           : 2024:10:03 04:58:35-04:00
File Inode Change Date/Time     : 2024:10:03 04:58:35-04:00
File Permissions                : -rw-rw-r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 600
Image Height                    : 600
Bit Depth                       : 8
Color Type                      : RGB
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Software                        : Adobe ImageReady
XMP Toolkit                     : Adobe XMP Core 5.3-c011 66.145661, 2012/02/06-14:56:27
Creator Tool                    : Adobe Photoshop CS6 (Windows)
Instance ID                     : xmp.iid:A5566E73B2B811E8BC7F9A4303DF1F9B
Document ID                     : xmp.did:A5566E74B2B811E8BC7F9A4303DF1F9B
Derived From Instance ID        : xmp.iid:A5566E71B2B811E8BC7F9A4303DF1F9B
Derived From Document ID        : xmp.did:A5566E72B2B811E8BC7F9A4303DF1F9B
Warning                         : [minor] Text/EXIF chunk(s) found after PNG IDAT (may be ignored by some readers)
Artist                          : picoCTF{s0_m3ta_d8944929}
Image Size                      : 600x600
Megapixels                      : 0.360
```

- ##### Viendo los metadatos de la imagen, obtenemos la bandera.
```
Flag: picoCTF{s0_m3ta_d8944929}
```
## Notas Adicionales
- Los **metadatos** de las fotos contienen información sobre el contenido, la ubicación, los ajustes de la cámara, las licencias y los derechos de autor, así como la información de contacto del fotógrafo.
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)