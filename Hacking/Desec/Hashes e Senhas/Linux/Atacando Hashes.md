<h1 align="center">Ferramentas para Atacar Hashes</h1>
<hr>

Quando a gente fala de ataque a hashes pra descobrir senhas , existem varias ferramentas 
vamos comentar as principais e mais conhecidas.

- john
Umas das primeiras ferramentas para quebra de hashs	 

```sh
john <HASH>
john --format=Raw-MD5 --wordlist
```

- hashcat
Uma exceltissima ferramentas pertimindo usar a GPU do computador para processar e fazer ataque de forca bruta

```sh
hashcat -m <TYPE CODE> <HASH> <WORDLIST> --force
hashcat -m 100 hash /usr/share/john/password.lst --force
```
