## Objetivo
There is a nice program that you can talk to by using this command in a shell: `$ nc mercury.picoctf.net 49039`, but it doesn't speak English...
## Solución
```
mklinux@DESKTOP-L3T98RN:/mnt/c/Users/Miguel/Documents/SRSS$ nc mercury.picoctf.net 49039
112
105
99
111
67
84
70
123
103
48
48
100
95
107
49
116
116
121
33
95
110
49
99
51
95
107
49
116
116
121
33
95
51
100
56
52
101
100
99
56
125
10
```

- ##### Se convertirá la serie de números de ASCII a Texto.
```
Cadena de números: 112, 105, 99, 111, 67, 84, 70, 123, 103, 48, 48, 100, 95, 107, 49, 116, 116, 121, 33, 95, 110, 49, 99, 51, 95, 107, 49, 116, 116, 121, 33, 95, 51, 100, 56, 52, 101, 100, 99, 56, 125, 10

Texto normal: picoCTF{g00d_k1tty!_n1c3_k1tty!_3d84edc8}
```
## Notas Adicionales
- Es un código estándar definido y establecido para representar los caracteres (letras, números, signos de puntuación, caracteres especiales, etc.) de forma numérica.
## Referencias
- [PicoCTF](https://play.picoctf.org)
- [Convertidor ASCII a Texto](https://www.duplichecker.com/ascii-to-text.php)