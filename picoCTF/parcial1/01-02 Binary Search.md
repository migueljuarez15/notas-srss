## Objetivo
Want to play a game? As you use more of the shell, you might be interested in how they work! Binary search is a classic algorithm used to quickly find an item in a sorted list. Can you find the flag? You'll have 1000 possibilities and only 10 guesses.Cyber security often has a huge amount of data to look through - from logs, vulnerability reports, and forensics. Practicing the fundamentals manually might help you in the future when you have to write your own tools!

`ssh -p 57175 ctf-player@atlas.picoctf.net`

Using the password `1ad5be0d`. Accept the fingerprint with `yes`, and `ls` once connected to begin. Remember, in a shell, passwords are hidden!
## Solución
```
┌──(kali㉿kali)-[~]
└─$ ssh -p 57175 ctf-player@atlas.picoctf.net
ctf-player@atlas.picoctf.net's password: 
Welcome to the Binary Search Game!
I'm thinking of a number between 1 and 1000.
Enter your guess: 500
Lower! Try again.
Enter your guess: 300
Lower! Try again.
Enter your guess: 100
Lower! Try again.
Enter your guess: 50
Higher! Try again.
Enter your guess: 60
Higher! Try again.
Enter your guess: 80
Congratulations! You guessed the correct number: 80
Here's your flag: picoCTF{g00d_gu355_3af33d18}
Connection to atlas.picoctf.net closed.
```
## Notas Adicionales
- El algoritmo de búsqueda binaria lo que hace es **repetidamente apuntar al centro de la estructura de búsqueda y dividir el espacio restante por la mitad, así hasta encontrar el valor buscado**.
## Referencias
- [PicoCTF](https://play.picoctf.org)