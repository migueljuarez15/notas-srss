## Objetivo
Unzip this archive and find the flag.
## Solución
```
┌──(kali㉿kali)-[~]
└─$ cd Downloads    
                                                                             
┌──(kali㉿kali)-[~/Downloads]
└─$ unzip big-zip-files.zip 
Archive:  big-zip-files.zip
   creating: big-zip-files/
 extracting: big-zip-files/jpvaawkrpno.txt  
  inflating: big-zip-files/oxbcyjsy.txt  
  inflating: big-zip-files/hllhxlvvdgiii.txt  
  inflating: big-zip-files/bdvnqbuutefealgveyiqd.txt  
  inflating: big-zip-files/fudfsewmaafsbniiyktzr.txt  
   creating: big-zip-files/folder_fqmjtuthge/
  inflating: big-zip-files/folder_fqmjtuthge/file_eaigogtrdslbxenbnfisxepj.txt  
  inflating: big-zip-files/folder_fqmjtuthge/file_ygocxgpzuxqjwfs.txt  
  inflating: big-zip-files/folder_fqmjtuthge/file_lqqprxhjtarithwygepdnlf.txt
  .   .   .   
 extracting: big-zip-files/folder_wdhgdgrbfc/finitvya.txt  
  inflating: big-zip-files/folder_wdhgdgrbfc/bondkyoxvdcgxyq.txt  
  inflating: big-zip-files/folder_wdhgdgrbfc/file_hacfyxtdwkdiycfwatiyvusg.txt  
  inflating: big-zip-files/folder_wdhgdgrbfc/file_jdlhinpycace.txt  
  inflating: big-zip-files/folder_wdhgdgrbfc/gnsnwwhmlslslscapr.txt  
  inflating: big-zip-files/folder_wdhgdgrbfc/file_ximyquuowm.txt  
  inflating: big-zip-files/folder_wdhgdgrbfc/siizcxeduftjnvian.txt  
  inflating: big-zip-files/mktyhgmedcj.txt  
                                                                             
┌──(kali㉿kali)-[~/Downloads]
└─$ grep -r big-zip-files -e pico
big-zip-files/folder_pmbymkjcya/folder_cawigcwvgv/folder_ltdayfmktr/folder_fnpfclfyee/whzxrpivpqld.txt:information on the record will last a billion years. Genes and brains and books encode picoCTF{gr3p_15_m4g1c_ef8790dc}
```
## Notas Adicionales
- **grep** - Muestra la línea del texto donde se buscó la palabra.
## Referencias
- [PicoCTF](https://play.picoctf.org)