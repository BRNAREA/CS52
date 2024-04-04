
Em alguns casos se o firewall estiver mal configurado ele deixara passar a requisicao caso venha de alguma porta de origem.

Portas que podemos tentar : 53,80,443

```bash
nmap -v -sS -Pn -g 53 172.18.0.2
ou
nmap -v -sS -Pn --source-port 53 172.18.0.2
```

```bash
nc -vn -p 53 172.18.0.2 8180 > /var/www/html/recon.html

service apache2 start
```

Eh sempre interessante testar isso quando tem um firewall , testar portas de origem para ver como  o firewall vai se comportar, se dermos sorte e o firewall estiver mal configurado vamos conseguir varrer os servicos que estao atras do firewall

