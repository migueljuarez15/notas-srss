## Objetivo
Connect to this PostgreSQL server and find the flag!
## Solución
```
──(kali㉿kali)-[~/picoCTF]
└─$ psql -h saturn.picoctf.net -p 58059 -U postgres pico
Password for user postgres: postgres
psql (16.3 (Debian 16.3-1), server 15.2 (Debian 15.2-1.pgdg110+1))
Type "help" for help.

pico=# \dt
         List of relations
 Schema | Name  | Type  |  Owner   
--------+-------+-------+----------
 public | flags | table | postgres
(1 row)

pico=# select * from flags;
 id | firstname | lastname  |                address                 
----+-----------+-----------+----------------------------------------
  1 | Luke      | Skywalker | picoCTF{L3arN_S0m3_5qL_t0d4Y_73b0678f}
  2 | Leia      | Organa    | Alderaan
  3 | Han       | Solo      | Corellia
```

- ##### Luego de buscar en la base de datos, obtenemos la bandera.
```
Flag: picoCTF{L3arN_S0m3_5qL_t0d4Y_73b0678f}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)