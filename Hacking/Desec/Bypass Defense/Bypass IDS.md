
<h1 align="center">Bypass</h1>
<hr>

O Snort possui alguns padroes em suas regras , e com isso podemos contorna-las , um exemplo disso seria a regra de alerta ICMP , veja abaixo a regra tem um padrao que seria o conteudo "10 12 13 14 15 16 17 18 1A 1B 1C 1D 1E 1F"

![[mpv-shot0001 5.jpg]]

Para contornar essa regras existe um parametro do ping que permite mudar esse conteudo

```bash
ping -c1 -p "646566768" 178.18.0.2
```

```sh
hping3 --icmp -C 8 -K 1  <IP>
```