<h1 align="center"> Quebrando hashes do Windows</h1>
<hr>

Uma vez que a gente ja descobriu como obter os hashes vamos ver como a gente faz pra quebrar esses hashes , descobrir senhas e ver como a gente trabalha com eles obtidos no Windows.

```sh
john --format=lm hashlm ; para hashes lm
```

```sh
john --format=nt --wordlist=/usr/share/wordlists/rockyou.txt hash10
```