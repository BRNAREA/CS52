<h2 align="center">Enumerando MYSQL</h2>
<hr>

```ad-info
PORTA PADRAO: 3306
```

```bash
nmap --open -sS -p 3306 -Pn <IP>
mysql -h <IP> -u mysql -p ;; [ -h=host, -u=user, -p=basededados]

show databases;
use owasp10;
show tables;
select * from credit_cards;
```