## Objetivo
Download this image file and find the flag.

- [Download image file](https://artifacts.picoctf.net/c/100/drawing.flag.svg)
## Solución
```
──(kali㉿kali)-[~/picoCTF/Forensics/Enhance]
└─$ wget https://artifacts.picoctf.net/c/100/drawing.flag.svg 
--2024-10-26 01:18:13--  https://artifacts.picoctf.net/c/100/drawing.flag.svg
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 13.225.222.120, 13.225.222.28, 13.225.222.105, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|13.225.222.120|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4149 (4.1K) [application/octet-stream]
Saving to: ‘drawing.flag.svg’

drawing.flag.svg             100%[============================================>]   4.05K  --.-KB/s    in 0s      

2024-10-26 01:18:13 (105 MB/s) - ‘drawing.flag.svg’ saved [4149/4149]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/Enhance]
└─$ file drawing.flag.svg 
drawing.flag.svg: SVG Scalable Vector Graphics image
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/Enhance]
└─$ open drawing.flag.svg
                                                                                                                       
┌──(kali㉿kali)-[~/picoCTF/Forensics/Enhance]
└─$ exiftool drawing.flag.svg                                    
ExifTool Version Number         : 12.76
File Name                       : drawing.flag.svg
Directory                       : .
File Size                       : 4.1 kB
File Modification Date/Time     : 2023:03:15 23:15:29-04:00
File Access Date/Time           : 2024:10:26 01:18:24-04:00
File Inode Change Date/Time     : 2024:10:26 01:18:13-04:00
File Permissions                : -rw-rw-r--
File Type                       : SVG
File Type Extension             : svg
MIME Type                       : image/svg+xml
Xmlns                           : http://www.w3.org/2000/svg
Image Width                     : 210mm
Image Height                    : 297mm
View Box                        : 0 0 210 297
SVG Version                     : 1.1
ID                              : svg8
Version                         : 0.92.5 (2060ec1f9f, 2020-04-08)
Docname                         : drawing.svg
Metadata ID                     : metadata5
Work Format                     : image/svg+xml
Work Type                       : http://purl.org/dc/dcmitype/StillImage
Work Title                      : 
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/Enhance]
└─$ cat drawing.flag.svg
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!-- Created with Inkscape (http://www.inkscape.org/) -->

<svg
   xmlns:dc="http://purl.org/dc/elements/1.1/"
   xmlns:cc="http://creativecommons.org/ns#"
.   .   .
         style="font-size:0.00352781px;line-height:1.25;fill:#ffffff;stroke-width:0.26458332;"
         id="tspan3748">p </tspan><tspan
         sodipodi:role="line"
         x="107.43014"
         y="132.08942"
         style="font-size:0.00352781px;line-height:1.25;fill:#ffffff;stroke-width:0.26458332;"
         id="tspan3754">i </tspan><tspan
         sodipodi:role="line"
         x="107.43014"
         y="132.09383"
         style="font-size:0.00352781px;line-height:1.25;fill:#ffffff;stroke-width:0.26458332;"
         id="tspan3756">c </tspan><tspan
         sodipodi:role="line"
         x="107.43014"
         y="132.09824"
         style="font-size:0.00352781px;line-height:1.25;fill:#ffffff;stroke-width:0.26458332;"
         id="tspan3758">o </tspan><tspan
         sodipodi:role="line"
         x="107.43014"
         y="132.10265"
         style="font-size:0.00352781px;line-height:1.25;fill:#ffffff;stroke-width:0.26458332;"
         id="tspan3760">C </tspan><tspan
         sodipodi:role="line"
         x="107.43014"
         y="132.10706"
         style="font-size:0.00352781px;line-height:1.25;fill:#ffffff;stroke-width:0.26458332;"
         id="tspan3762">T </tspan><tspan
         sodipodi:role="line"
         x="107.43014"
         y="132.11147"
         style="font-size:0.00352781px;line-height:1.25;fill:#ffffff;stroke-width:0.26458332;"
         id="tspan3764">F { 3 n h 4 n </tspan><tspan
         sodipodi:role="line"
         x="107.43014"
         y="132.11588"
         style="font-size:0.00352781px;line-height:1.25;fill:#ffffff;stroke-width:0.26458332;"
         id="tspan3752">c 3 d _ a a b 7 2 9 d d }</tspan></text>
  </g>
</svg>
```

- ##### Después de analizar el código fuente de la imagen, mediante los "< span >" obtenemos la bandera.
```
Flag: picoCTF{3nh4nc3d_aab729dd}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)