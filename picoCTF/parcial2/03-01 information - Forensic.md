## Objetivo
Files can always be changed in a secret way. Can you find the flag? [cat.jpg](https://mercury.picoctf.net/static/c28a959c5605d5f67480d5dd3a77f302/cat.jpg)
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Forensics/parcial2]
└─$ wget https://mercury.picoctf.net/static/c28a959c5605d5f67480d5dd3a77f302/cat.jpg
--2024-10-26 00:50:44--  https://mercury.picoctf.net/static/c28a959c5605d5f67480d5dd3a77f302/cat.jpg
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 878136 (858K) [application/octet-stream]
Saving to: ‘cat.jpg’

cat.jpg                      100%[============================================>] 857.55K  1.43MB/s    in 0.6s    

2024-10-26 00:50:45 (1.43 MB/s) - ‘cat.jpg’ saved [878136/878136]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/parcial2]
└─$ file cat.jpg       
cat.jpg: JPEG image data, JFIF standard 1.02, aspect ratio, density 1x1, segment length 16, baseline, precision 8, 2560x1598, components 3
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/parcial2]
└─$ open cat.jpg                        
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/parcial2]
└─$ exiftool cat.jpg     
ExifTool Version Number         : 12.76
File Name                       : cat.jpg
Directory                       : .
File Size                       : 878 kB
File Modification Date/Time     : 2021:03:15 14:24:46-04:00
File Access Date/Time           : 2024:10:26 00:50:53-04:00
File Inode Change Date/Time     : 2024:10:26 00:50:45-04:00
File Permissions                : -rw-rw-r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.02
Resolution Unit                 : None
X Resolution                    : 1
Y Resolution                    : 1
Current IPTC Digest             : 7a78f3d9cfb1ce42ab5a3aa30573d617
Copyright Notice                : PicoCTF
Application Record Version      : 4
XMP Toolkit                     : Image::ExifTool 10.80
License                         : cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9
Rights                          : PicoCTF
Image Width                     : 2560
Image Height                    : 1598
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 2560x1598
Megapixels                      : 4.1
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/parcial2]
└─$ echo cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9 | base64 -d
picoCTF{the_m3tadata_1s_modified}
```

- ##### Después de decodificar el texto encontrado en el apartado de "License" mediante base64, obtenemos la bandera.
```
Flag: picoCTF{the_m3tadata_1s_modified}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)