<h2 align="center"> Metasploit Framework</h2>
<hr>

Vamos suport que voce ta buscando  por um exploit independente da falha que for 

```sh
searchsploit proftp
```

o comando `msfdb` eh para voce gerenciar sua base de dados do metasploit

vamos agora atualizar o metasploit

```sh
sudo pacman -Syu; sudo pacman -S metasploit-framework
```

agora vamos iniciar o banco de dados.

Antes de iniciar o PostgreSQL pela primeira vez, é necessário inicializar o banco de dados com o comando `initdb`. Este comando cria o diretório de dados necessário com a estrutura correta e os arquivos de configuração iniciais.

A mensagem de erro sugere o seguinte comando para inicializar o banco de dados:

```sh
su -l postgres -c "initdb --locale=C.UTF-8 --encoding=UTF8 -D '/var/lib/postgres/data'"

# troque para o usuario postgres e inicie tambem o db
sudo -iu postgres
initdb --locale=C.UTF-8 --encoding=UTF8 -D '/var/lib/postgres/data'

sudo systemctl enable postgresql
sudo systemctl start postgresql

msfdb init
msfconsole
```

