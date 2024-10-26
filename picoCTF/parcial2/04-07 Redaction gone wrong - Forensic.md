## Objetivo
Now you DON’T see me. This [report](https://artifacts.picoctf.net/c/84/Financial_Report_for_ABC_Labs.pdf) has some critical data in it, some of which have been redacted correctly, while some were not. Can you find an important key that was not redacted properly?
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Forensics/RedactionGoneWrong]
└─$ wget https://artifacts.picoctf.net/c/84/Financial_Report_for_ABC_Labs.pdf                             
--2024-10-26 04:09:41--  https://artifacts.picoctf.net/c/84/Financial_Report_for_ABC_Labs.pdf
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 13.225.222.28, 13.225.222.125, 13.225.222.105, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|13.225.222.28|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 34915 (34K) [application/octet-stream]
Saving to: ‘Financial_Report_for_ABC_Labs.pdf’

Financial_Report_for_ABC_Lab 100%[============================================>]  34.10K  --.-KB/s    in 0.04s   

2024-10-26 04:09:42 (892 KB/s) - ‘Financial_Report_for_ABC_Labs.pdf’ saved [34915/34915]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/RedactionGoneWrong]
└─$ file Financial_Report_for_ABC_Labs.pdf
Financial_Report_for_ABC_Labs.pdf: PDF document, version 1.7, 1 page(s)
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Forensics/RedactionGoneWrong]
└─$ open Financial_Report_for_ABC_Labs.pdf
```

- ##### Luego de abrir el PDF, y de ir buscando en los recuadros negros cuando los seleccionamos con el ratón, obtenemos la bandera.
```
Flag: picoCTF{C4n_Y0u_S33_m3_fully}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)