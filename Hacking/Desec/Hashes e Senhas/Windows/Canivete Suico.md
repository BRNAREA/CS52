<h1 align="center">Swiss Army Knife para Pentest em Redes Windows</h1>
<hr>

Existe uma ferramenta como se fosse um canivete suico chamada <span style='color:var(--mk-color-red)'>crackmapexec</span> .

Vamos procurar por hosts que tenham smb ativo na rede inteira
```sh
apt install crackmapexec
> crackmapexec smb 172.16.1.0/24
```

Aqui seria um primeiro passo , estamos falando de uma parte mais e enumeracao e mapeamento de redes para smb por exemplo.

Essa ferramenta tem muitas funcionalidades embutidas. Voce pode ver com o seguinte comando:

```sh
crackmapexec -L
```