## Objetivo
[🥛](http://mercury.picoctf.net:48319/)
## Solución
- ##### Se descarga la imagen del sitio, y podemos observar que se le puede hacer esteganografía, por lo que usaremos "zsteg".
```
┌──(kali㉿kali)-[~/picoCTF/Milkslap]
└─$ ls
concat_v.png
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Milkslap]
└─$ strings concat_v.png -n 15                                                                
pu59;;;::>>>~wrv5
s{qq~rrr|||zzz9
Nr&UTTTTTTTTTTTT<
DIlY!^D./{&&fU/
Qvu}}x89???;;;8
F`@"c(3uc_]-kg7
1Fk}rrrzzztT]^.
\-0sUUUU]]Ujp6M
Xub-K>,kArD]]]m65"$I:J3
 Aj6f`gi&3iLfH)=N
gVJSWTeY^_____/
        2"Cr}j0]/j(,bMwL$
~zzzzzzxxxzzz~^S
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Milkslap]
└─$ zsteg -a concat_v.png | grep "picoCTF"                                                    
/var/lib/gems/3.1.0/gems/zpng-0.4.5/lib/zpng/scan_line.rb:303:in `upto': stack level too deep (SystemStackError)
        from /var/lib/gems/3.1.0/gems/zpng-0.4.5/lib/zpng/scan_line.rb:303:in `decoded_bytes'
        from /var/lib/gems/3.1.0/gems/zpng-0.4.5/lib/zpng/scan_line/mixins.rb:17:in `prev_scanline_byte'
        from /var/lib/gems/3.1.0/gems/zpng-0.4.5/lib/zpng/scan_line.rb:377:in `prev_scanline_byte'
        from /var/lib/gems/3.1.0/gems/zpng-0.4.5/lib/zpng/scan_line.rb:319:in `block in decoded_bytes'
        from /var/lib/gems/3.1.0/gems/zpng-0.4.5/lib/zpng/scan_line.rb:318:in `upto'
        from /var/lib/gems/3.1.0/gems/zpng-0.4.5/lib/zpng/scan_line.rb:318:in `decoded_bytes'
        from /var/lib/gems/3.1.0/gems/zpng-0.4.5/lib/zpng/scan_line/mixins.rb:17:in `prev_scanline_byte'
        from /var/lib/gems/3.1.0/gems/zpng-0.4.5/lib/zpng/scan_line.rb:377:in `prev_scanline_byte'
         ... 9483 levels...
        from /var/lib/gems/3.1.0/gems/zsteg-0.2.13/lib/zsteg.rb:26:in `run'
        from /var/lib/gems/3.1.0/gems/zsteg-0.2.13/bin/zsteg:8:in `<top (required)>'
        from /usr/local/bin/zsteg:25:in `load'
        from /usr/local/bin/zsteg:25:in `<main>'
```

- ##### Una vez decodificada, obtenemos la bandera.
```
Flag: picoCTF{imag3_m4n1pul4t10n_sl4p5}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)