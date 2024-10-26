## Objetivo
Download this image and find the flag.

- [Download image](https://artifacts.picoctf.net/c/216/pico.flag.png)
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Forensics/St3g0]
└─$ wget https://artifacts.picoctf.net/c/216/pico.flag.png                   
--2024-10-26 04:15:07--  https://artifacts.picoctf.net/c/216/pico.flag.png
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.26, 3.161.55.61, 3.161.55.64, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.26|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13441 (13K) [application/octet-stream]
Saving to: ‘pico.flag.png’

pico.flag.png                100%[============================================>]  13.13K  --.-KB/s    in 0s      

2024-10-26 04:15:08 (202 MB/s) - ‘pico.flag.png’ saved [13441/13441]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/St3g0]
└─$ file pico.flag.png                    
pico.flag.png: PNG image data, 585 x 172, 8-bit/color RGBA, non-interlaced
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/St3g0]
└─$ open pico.flag.png                    
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/St3g0]
└─$ exiftool pico.flag.png                                          
ExifTool Version Number         : 12.76
File Name                       : pico.flag.png
Directory                       : .
File Size                       : 13 kB
File Modification Date/Time     : 2023:08:04 16:36:17-04:00
File Access Date/Time           : 2024:10:26 04:15:15-04:00
File Inode Change Date/Time     : 2024:10:26 04:15:08-04:00
File Permissions                : -rw-rw-r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 585
Image Height                    : 172
Bit Depth                       : 8
Color Type                      : RGB with Alpha
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Image Size                      : 585x172
Megapixels                      : 0.101
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/St3g0]
└─$ zsteg -a pico.flag.png | grep "picoCTF"
b1,rgb,lsb,xy       .. text: "picoCTF{7h3r3_15_n0_5p00n_a1062667}$t3g0"
/var/lib/gems/3.1.0/gems/zsteg-0.2.13/lib/zsteg/checker/wbstego.rb:41:in `to_s': stack level too deep (SystemStackError)
        from /var/lib/gems/3.1.0/gems/iostruct-0.1.3/lib/iostruct.rb:159:in `inspect'
        from /var/lib/gems/3.1.0/gems/zsteg-0.2.13/lib/zsteg/checker/wbstego.rb:41:in `to_s'
        from /var/lib/gems/3.1.0/gems/iostruct-0.1.3/lib/iostruct.rb:159:in `inspect'
        from /var/lib/gems/3.1.0/gems/zsteg-0.2.13/lib/zsteg/checker/wbstego.rb:41:in `to_s'
        from /var/lib/gems/3.1.0/gems/iostruct-0.1.3/lib/iostruct.rb:159:in `inspect'
        from /var/lib/gems/3.1.0/gems/zsteg-0.2.13/lib/zsteg/checker/wbstego.rb:41:in `to_s'
        from /var/lib/gems/3.1.0/gems/iostruct-0.1.3/lib/iostruct.rb:159:in `inspect'
        from /var/lib/gems/3.1.0/gems/zsteg-0.2.13/lib/zsteg/checker/wbstego.rb:41:in `to_s'
         ... 10066 levels...
        from /var/lib/gems/3.1.0/gems/zsteg-0.2.13/lib/zsteg.rb:26:in `run'
        from /var/lib/gems/3.1.0/gems/zsteg-0.2.13/bin/zsteg:8:in `<top (required)>'
        from /usr/local/bin/zsteg:25:in `load'
        from /usr/local/bin/zsteg:25:in `<main>'
```

- ##### Después de usar la gema "zsteg" en la imagen, obtenemos la bandera.
```
Flag: picoCTF{7h3r3_15_n0_5p00n_a1062667}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)