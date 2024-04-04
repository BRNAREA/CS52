Mapear hosts de forma rapida

```bash
descobrir hosts ativos

nmap -v -sn 192.168.0.1/24 -oG ativos.txt

grep "Up" ativos.txt | cut -d " " -f 2 > hosts

;; Saber todos os hosts com webserver ativo

nmap -sSV -p 80 --open -Pn -iL hosts -oG web.txt (opcao -V traz o banner vai conseguir detectar a versao do webserver)

grep "IIS" web.txt
```