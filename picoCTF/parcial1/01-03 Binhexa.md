## Objetivo
How well can you perfom basic binary operations?

Additional details will be available after launching your challenge instance.
## Solución
```
mklinux@DESKTOP-TCK94Q6:/mnt/c/Users/elmel$ nc titan.picoctf.net 59204

Welcome to the Binary Challenge!"
Your task is to perform the unique operations in the given order and find the final result in hexadecimal that yields the flag.

Binary Number 1: 10101001
Binary Number 2: 11101011


Question 1/6:
Operation 1: '*'
Perform the operation on Binary Number 1&2.
Enter the binary result: 1001101100100011
Correct!

Question 2/6:
Operation 2: '<<'
Perform a left shift of Binary Number 1 by 1 bits.
Enter the binary result: 101010010
Correct!

Question 3/6:
Operation 3: '>>'
Perform a right shift of Binary Number 2 by 1 bits.
Enter the binary result: 1110101
Correct!

Question 4/6:
Operation 4: '|'
Perform the operation on Binary Number 1&2.
Enter the binary result: 11101011
Correct!

Question 5/6:
Operation 5: '+'
Perform the operation on Binary Number 1&2.
Enter the binary result: 110010100
Correct!

Question 6/6:
Operation 6: '&'
Perform the operation on Binary Number 1&2.
Enter the binary result: 10101001
Correct!

Enter the results of the last operation in hexadecimal: A9

Correct answer!
The flag is: picoCTF{b1tw^3se_0p3eR@tI0n_su33essFuL_d6f8047e}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)