## Objetivo
Can you crack the password to get the flag?
There are 7 potential passwords with 1 being correct. 
You can find these by examining the password checker script.
## Solución
``` bash
mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ wget https://artifacts.picoctf.net/c/16/level3.py
--2024-09-17 01:32:02--  https://artifacts.picoctf.net/c/16/level3.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.225.62, 3.161.225.3, 3.161.225.60, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.225.62|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1337 (1.3K) [application/octet-stream]
Saving to: ‘level3.py’

level3.py                     100%[=================================================>]   1.31K  --.-KB/s    in 0s

2024-09-17 01:32:02 (489 MB/s) - ‘level3.py’ saved [1337/1337]

mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ wget https://artifacts.picoctf.net/c/16/level3.flag.txt.enc
--2024-09-17 01:32:10--  https://artifacts.picoctf.net/c/16/level3.flag.txt.enc
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.225.62, 3.161.225.3, 3.161.225.60, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.225.62|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 31 [application/octet-stream]
Saving to: ‘level3.flag.txt.enc’

level3.flag.txt.enc           100%[=================================================>]      31  --.-KB/s    in 0s

2024-09-17 01:32:10 (14.8 MB/s) - ‘level3.flag.txt.enc’ saved [31/31]

mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ wget https://artifacts.picoctf.net/c/16/level3.hash.bin
--2024-09-17 01:32:18--  https://artifacts.picoctf.net/c/16/level3.hash.bin
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.225.62, 3.161.225.3, 3.161.225.60, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.225.62|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16 [application/octet-stream]
Saving to: ‘level3.hash.bin’

level3.hash.bin               100%[=================================================>]      16  --.-KB/s    in 0s

2024-09-17 01:32:19 (5.75 MB/s) - ‘level3.hash.bin’ saved [16/16]

mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ nano level3.py

import hashlib

### THIS FUNCTION WILL NOT HELP YOU FIND THE FLAG --LT ########################
def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])
###############################################################################

flag_enc = open('level3.flag.txt.enc', 'rb').read()
correct_pw_hash = open('level3.hash.bin', 'rb').read()

def hash_pw(pw_str):
    pw_bytes = bytearray()
    pw_bytes.extend(pw_str.encode())
	m = hashlib.md5()
    m.update(pw_bytes)
    return m.digest()

def level_3_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    user_pw_hash = hash_pw(user_pw)

    if( user_pw_hash == correct_pw_hash ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")

level_3_pw_check()


# The strings below are 7 possibilities for the correct password.
#   (Only 1 is correct)
pos_pw_list = ["6997", "3ac8", "f0ac", "4b17", "ec27", "4e66", "865e"]

mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ python3 level3.py
Please enter correct password for flag: 6997
That password is incorrect
mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ python3 level3.py
Please enter correct password for flag: 3ac8
That password is incorrect
mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ python3 level3.py
Please enter correct password for flag: f0ac
That password is incorrect
mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ python3 level3.py
Please enter correct password for flag: 4b17
That password is incorrect
mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ python3 level3.py
Please enter correct password for flag: ec27
That password is incorrect
mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ python3 level3.py
Please enter correct password for flag: 4e66
That password is incorrect
mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ python3 level3.py
Please enter correct password for flag: 865e
Welcome back... your flag, user:
picoCTF{m45h_fl1ng1ng_2b072a90}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)