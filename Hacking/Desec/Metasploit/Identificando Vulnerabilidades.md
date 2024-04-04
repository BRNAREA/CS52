<h1 align="center">Identificando Vulnerabilidades</h1>
<hr>

Adicionando uma informacao:

```sh
msf5> auxiliary(scanner/smb/smb_version) > hosts -i "Samba 3.0" <IP/HOST>
hosts
```

Se quisermos buscar vulnerabilidades nessa versao em especifico podemos fazer 

```sh
# Buscando por vulnerabilidades no Samba 3.0
msf5> search type:exploit samba
```

```ad-important
title: Tenha certeza do que esta fazendo!

Sempre procure por vulnerabilidades que condizem com a versao do servico , pois se voce nao fizer isso pode ser e muito provavelmente sera detectado por IPS, IDS, FWs, WAFs... 

A boa pratica eh que voce tenha certeza do que voce esta fazendo
```

Entao vamos buscar por exploits que condizem com a versao 3.0 do samba.

```sh
msf5> search type:exploit fullname:"Samba 3.0.20"
```

Ainda no tipo auxiliar vamos pesquisar por smb ja que a maioria dos hosts usam smb:

```
search type:auxiliary smb
use auxiliary/scanner/smb/smb_ms17_010

# ver informaces sobre o modulo auxiliar
msf5> auxiliaryt(scanner/smb/smb_ms17_010) > info

# usando nos hosts
msf5> auxiliaryt(scanner/smb/smb_ms17_010) > services -p 445 --rhosts
msf5> show options
msf5> auxiliaryt(scanner/smb/smb_ms17_010) > run
msf5> auxiliaryt(scanner/smb/smb_ms17_010) > vulns
```