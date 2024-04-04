<h1 align="center"> Identificando os Hashes</h1>
<hr>

```ad-quote

Imagine a seguinte situacao , voce compremete um ambiente , ou voce tem acesso a um determinado sistema e ai a informacao que voce coleta seria algo semelhante a isso : `2385bd1542542aac275db5f88b8e3f788145c773da97a137131ac5433c0b9ed41f9704ff1a431f8473b6b82f9da963a270029a818bcfb299c857174b73a61a89` 

Voce bate o olho e nao sabe oque seria , ou o tipo de hash.
Eh necessario voce saber disso para que voce possa fazer o ataque naquele hash , porque imagina que voce vai pegar um worlist com varias senhas e tem que aplicar aquele mesmo algoritimo de hash que existe naquele servidor pra depois tentar fazer a comparacao , e descobrir aqueles hashes.

Entao existe alguns softwares que a gente pode utilizar.
```

Em sistemas Linux temos os seguintes:

- hashid
```sh
hashid 2385bd1542542aac275db5f88b8e3f788145c773da97a137131ac5433c0b9ed41f9704ff1a431f8473b6b82f9da963a270029a818bcfb299c857174b73a61a89
```

- hash-identifier
```sh
hash-identifier
HASH: 2385bd1542542aac275db5f88b8e3f788145c773da97a137131ac5433c0b9ed41f9704ff1a431f8473b6b82f9da963a270029a818bcfb299c857174b73a61a89

Possible Hashs:
[+] SHA-384
[+] SHA-384(HMAC)
```



