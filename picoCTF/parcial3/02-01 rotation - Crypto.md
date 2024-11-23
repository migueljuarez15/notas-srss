## Objetivo
You will find the flag after decrypting this file.
Download the encrypted flag [here](https://artifacts.picoctf.net/c/388/encrypted.txt).
## Solución
```
┌──(kali㉿kali)-[~/picoCTF/Crypto/rotation]
└─$ wget https://artifacts.picoctf.net/c/388/encrypted.txt
--2024-11-22 23:18:58--  https://artifacts.picoctf.net/c/388/encrypted.txt
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 13.225.222.120, 13.225.222.105, 13.225.222.125, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|13.225.222.120|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 37 [application/octet-stream]
Saving to: ‘encrypted.txt’

encrypted.txt                100%[============================================>]      37  --.-KB/s    in 0s      

2024-11-22 23:18:58 (40.7 MB/s) - ‘encrypted.txt’ saved [37/37]

                                                                                                                  
┌──(kali㉿kali)-[~/picoCTF/Crypto/rotation]
└─$ cat encrypted.txt   
xqkwKBN{z0bib1wv_l3kzgxb3l_25l7k61j}
```

- ##### Desencriptaremos el texto mediante ROT13 Brute Force.
```
MEDIANTE ROT13 BRUTE FORCE:
Amount =  1: yrlxLCO{a0cjc1xw_m3lahyc3m_25m7l61k}
Amount =  2: zsmyMDP{b0dkd1yx_n3mbizd3n_25n7m61l}
Amount =  3: atnzNEQ{c0ele1zy_o3ncjae3o_25o7n61m}
Amount =  4: buoaOFR{d0fmf1az_p3odkbf3p_25p7o61n}
Amount =  5: cvpbPGS{e0gng1ba_q3pelcg3q_25q7p61o}
Amount =  6: dwqcQHT{f0hoh1cb_r3qfmdh3r_25r7q61p}
Amount =  7: exrdRIU{g0ipi1dc_s3rgnei3s_25s7r61q}
Amount =  8: fyseSJV{h0jqj1ed_t3shofj3t_25t7s61r}
Amount =  9: gztfTKW{i0krk1fe_u3tipgk3u_25u7t61s}
Amount = 10: haugULX{j0lsl1gf_v3ujqhl3v_25v7u61t}
Amount = 11: ibvhVMY{k0mtm1hg_w3vkrim3w_25w7v61u}
Amount = 12: jcwiWNZ{l0nun1ih_x3wlsjn3x_25x7w61v}
Amount = 13: kdxjXOA{m0ovo1ji_y3xmtko3y_25y7x61w}
Amount = 14: leykYPB{n0pwp1kj_z3ynulp3z_25z7y61x}
Amount = 15: mfzlZQC{o0qxq1lk_a3zovmq3a_25a7z61y}
Amount = 16: ngamARD{p0ryr1ml_b3apwnr3b_25b7a61z}
Amount = 17: ohbnBSE{q0szs1nm_c3bqxos3c_25c7b61a}
Amount = 18: picoCTF{r0tat1on_d3crypt3d_25d7c61b}
Amount = 19: qjdpDUG{s0ubu1po_e3dszqu3e_25e7d61c}
Amount = 20: rkeqEVH{t0vcv1qp_f3etarv3f_25f7e61d}
Amount = 21: slfrFWI{u0wdw1rq_g3fubsw3g_25g7f61e}
Amount = 22: tmgsGXJ{v0xex1sr_h3gvctx3h_25h7g61f}
Amount = 23: unhtHYK{w0yfy1ts_i3hwduy3i_25i7h61g}
Amount = 24: voiuIZL{x0zgz1ut_j3ixevz3j_25j7i61h}
Amount = 25: wpjvJAM{y0aha1vu_k3jyfwa3k_25k7j61i}
```

- ##### Una vez utilizado el algoritmo ROT13 de fuerza bruta, en la rotación 18 obtenemos la bandera.
```
Flag: picoCTF{r0tat1on_d3crypt3d_25d7c61b}
```
## Notas Adicionales
## Referencias
- [PicoCTF](https://play.picoctf.org)