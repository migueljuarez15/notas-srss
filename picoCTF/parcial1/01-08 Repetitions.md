## Objetivo
Can you make sense of this file?
## Solución
```
┌──(kali㉿kali)-[~/Downloads]
└─$ ls -la
total 118520
drwxr-xr-x   5 kali kali      4096 Sep 16 18:20 .
drwx------  20 kali kali      4096 Sep 16 18:20 ..
drwxrwxr-x 121 kali kali     36864 May  3  2020 big-zip-files
-rw-rw-r--   1 kali kali   3182988 Sep 11 12:33 big-zip-files.zip
-rw-rw-r--   1 kali kali     19196 Mar 11  2024 challenge.zip
drwxr-xr-x   3 kali kali      4096 Mar 11  2024 drop-in
-rw-rw-r--   1 kali kali       349 Mar 15  2023 enc_flag
drwxrwxr-x   5 kali kali      4096 May 13  2022 files
-rw-rw-r--   1 kali kali   3995553 Aug  4  2023 files.zip
-rwxrwxr-x   1 kali kali 114091533 Sep 11 02:02 Obsidian-1.6.7.AppImage
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads]
└─$ cat enc_flag 
VmpGU1EyRXlUWGxTYmxKVVYwZFNWbGxyV21GV1JteDBUbFpPYWxKdFVsaFpWVlUxWVZaS1ZWWnVh
RmRXZWtab1dWWmtSMk5yTlZWWApiVVpUVm10d1VWZFdVa2RpYlZaWFZtNVdVZ3BpU0VKeldWUkNk
MlZXVlhoWGJYQk9VbFJXU0ZkcVRuTldaM0JZVWpGS2VWWkdaSGRXCk1sWnpWV3hhVm1KRk5XOVVW
VkpEVGxaYVdFMVhSbHBWV0VKVVZGWm9RMlZzV2tWUmJFNVNDbUpXV25wWmExSmhWMGRHZEdWRlZs
aGkKYlRrelZERldUMkpzUWxWTlJYTkxDZz09Cg==
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads]
└─$ base64 enc_flag
Vm1wR1UxRXlSWGxVV0d4VFlteEtWVll3WkZOV2JHeHlWMjFHVjFKdGVEQlViRnBQWVd4S2RGVnNh
RnBXVmxVeFdWWmFTMVpXV25WaApSbVJYWld0YWIxZFdXbXRTTWs1eVRsWldXQXBpVlZwVVZtMTBk
MVZXWkZkVmEyUnBZbFphV0ZadE5WZFZaM0JwVTBWS2VsZFdVa05rCk1sWlhWbGhvV0dKWVFrOVZi
RkpYVTBaa2NWUnVUbGRhTTBKWlZXcEdTMlZXV2tkYVNHUlhDazFzV25wV1YzaGhWbTFLUms1WE9W
VlcKVmtwRVZHeGFZVmRGTVZoU2JIQldWMFZLVlZaR1dtOVJNbFp6VjJ0V1VtSkZOVk5EYlVwWFYy
NXdXbUV4U21oV01HUkhaRWRXUmxacwphR2tLWWxScmVsWkVSbGRVTWtwelVXeFdUbEpZVGt4RFp6
MDlDZz09Cg==
                                                                                                                  
┌──(kali㉿kali)-[~/Downloads]
└─$ base64 -d enc_flag | base64 -d | base64 -d | base64 -d | base64 -d | base64 -d
picoCTF{base64_n3st3d_dic0d!n8_d0wnl04d3d_dfe803c6}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)