## Objetivo
This vault uses ASCII encoding for the password. The source code for this vault is here: [VaultDoor4.java](https://jupiter.challenges.picoctf.org/static/834acd392e0964a41f05790655a994b9/VaultDoor4.java)
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Reversing/vault-door-4]
└─$ wget https://jupiter.challenges.picoctf.org/static/834acd392e0964a41f05790655a994b9/VaultDoor4.java
--2024-10-28 13:42:38--  https://jupiter.challenges.picoctf.org/static/834acd392e0964a41f05790655a994b9/VaultDoor4.java
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1497 (1.5K) [application/octet-stream]
Saving to: ‘VaultDoor4.java’

VaultDoor4.java              100%[============================================>]   1.46K  --.-KB/s    in 0s      

2024-10-28 13:42:57 (28.4 MB/s) - ‘VaultDoor4.java’ saved [1497/1497]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/vault-door-4]
└─$ cat VaultDoor4.java
import java.util.*;

class VaultDoor4 {
    public static void main(String args[]) {
        VaultDoor4 vaultDoor = new VaultDoor4();
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter vault password: ");
        String userInput = scanner.next();
        String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
        if (vaultDoor.checkPassword(input)) {
            System.out.println("Access granted.");
        } else {
            System.out.println("Access denied!");
        }
    }

    // I made myself dizzy converting all of these numbers into different bases,
    // so I just *know* that this vault will be impenetrable. This will make Dr.
    // Evil like me better than all of the other minions--especially Minion
    // #5620--I just know it!
    //
    //  .:::.   .:::.
    // :::::::.:::::::
    // :::::::::::::::
    // ':::::::::::::'
    //   ':::::::::'
    //     ':::::'
    //       ':'
    // -Minion #7781
    public boolean checkPassword(String password) {
        byte[] passBytes = password.getBytes();
        byte[] myBytes = {
            106 , 85  , 53  , 116 , 95  , 52  , 95  , 98  ,
            0x55, 0x6e, 0x43, 0x68, 0x5f, 0x30, 0x66, 0x5f,
            0142, 0131, 0164, 063 , 0163, 0137, 0146, 064 ,
            'a' , '8' , 'c' , 'd' , '8' , 'f' , '7' , 'e' ,
        };
        for (int i=0; i<32; i++) {
            if (passBytes[i] != myBytes[i]) {
                return false;
            }
        }
        return true;
    }
}
```

- ##### Decodificaremos partes de la contraseña con diferentes métodos:
```
106 , 85  , 53  , 116 , 95  , 52  , 95  , 98  , --- DECIMAL
0x55, 0x6e, 0x43, 0x68, 0x5f, 0x30, 0x66, 0x5f, --- HEXADECIMAL
0142, 0131, 0164, 063 , 0163, 0137, 0146, 064 , --- OCTAL
'a' , '8' , 'c' , 'd' , '8' , 'f' , '7' , 'e' , --- CARACTERES NORMALES
```

- ##### Luego de decodificar la contraseña, la introducimos en el programa.
```
┌──(kali㉿kali)-[~/picoCTF/Reversing/vault-door-4]
└─$ javac VaultDoor4.java
Picked up _JAVA_OPTIONS: -Dawt.useSystemAAFontSettings=on -Dswing.aatext=true
                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Reversing/vault-door-4]
└─$ java VaultDoor4      
Picked up _JAVA_OPTIONS: -Dawt.useSystemAAFontSettings=on -Dswing.aatext=true
Enter vault password: picoCTF{jU5t_4_bUnCh_0f_bYt3s_f4a8cd8f7e}
Access granted.
```

- ##### Una vez introducida la contraseña decodificada, obtenemos la bandera.
```
Flag: picoCTF{jU5t_4_bUnCh_0f_bYt3s_f4a8cd8f7e}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [PicoCTF Writeups](https://www.youtube.com/playlist?list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&authuser=0)