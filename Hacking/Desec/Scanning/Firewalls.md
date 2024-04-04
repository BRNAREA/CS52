
<h4 align="center"> IPTables </h4>
Para configurar nosso servidor e deixalo mais seguro , utilizaremos o IP Tables

```
iptables -P INPUT DROP [ -P=Policy INPUT=Entrada DROP=Rejeite] ou seja rejeite todos pacotes na entrada , assim os servicos que estao expostos estarao "seguros".

Se quisermos permitir alguma porta e protocolo fazemos
iptables -A INPUT -p tcp --dport 80 -j ACCEPT ou DROP [ -A adicionar INPUT=entrada -p=protocolo tcp --dport=porta destino 80 -j=acao ACEITAR ou REJEITAR]


```

Para configurar o iptables para bloquear todo o tráfego, exceto para as portas que você listou (8080, 5901, 3350 e 3389), você pode seguir os passos abaixo. Este exemplo assume que você deseja manter abertas as conexões para qualquer endereço IP nessas portas específicas e que você está aplicando estas regras na máquina que está escutando nessas portas.

### Passo 1: Definir políticas padrão para DROP

Primeiro, configure as políticas padrão das cadeias INPUT, FORWARD e OUTPUT para DROP. Isso bloqueará todo o tráfego, exceto o que for explicitamente permitido.

```bash
sudo iptables -P INPUT DROP 
sudo iptables -P FORWARD DROP 
sudo iptables -P OUTPUT ACCEPT
```


### Passo 2: Permitir tráfego essencial

Agora, adicione regras para permitir o tráfego nas portas que você listou como essenciais.

```bash
# Permitir tráfego local 
sudo iptables -A INPUT -i lo -j ACCEPT 

# Permitir conexões estabelecidas e relacionadas 
sudo iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT  

# Permitir tráfego nas portas especificadas 
sudo iptables -A INPUT -p tcp --dport 8080 -j ACCEPT 
sudo iptables -A INPUT -p tcp --dport 5901 -j ACCEPT 
sudo iptables -A INPUT -p tcp --dport 3350 -j ACCEPT 
sudo iptables -A INPUT -p tcp --dport 3389 -j ACCEPT
```

```ad-important
title: Port unreacheable
Para saber se uma porta esta com firewall em REJECT o scanner de porta nos retornara port-unreach, isso eh um comportamento de quando estamos em REJECT
```

