<h2 align="center"> NFS - NETWORK FILE SYSTEM </h2>
<hr>

```ad-info
title: NFS

Porta padrao: 2049 (tcp)
```

Protocolo desenvolvido para compartilhamento de  arquivos entre sistemas  em uma rede local (linux).

Vamo enumeralo:

```sh
nmap --open -sS -p 2049 -Pn 172.16.1.0/24
```

Primeira coisa que podemos fazer eh ver as versoes que esse protoclo suporta

``rpcinfo -p <IPADDR> | grep nfs`` 

Vendo as versoes disponiveis , eh interessante pra gente porque depois a gente na hora da montagem desse compartilhamento , uma vez que identificamos o protocolo esta em execucao depois a gente tem que identificar se tem compartilhamentos exportados ou seja disponiveis para que a gente possa tentar montalos e conecta-lo neles.

Depois podemos usar o comando ``showmount -e 172.16.1.5 -> vamos ver quais compartilhamentos estao compartilhados no sistema`` para ver mais detalhes sobre esse host

Se o sistema estiver com a raiz compartilhada ou seja ``Export list for <IPADDR> / *`` se conseguirmos montar a raiz vamos ter acesso a todo o sistema.


```bash
mkdir -p /tmp/nfs
mount -t nfs -o nfsvers=2,3,4 <IPADDR>:/ /tmp/nfs
```

``umount /tmp/nfs``


pode configurar o NFS para compartilhar diretórios sem especificar um host específico, permitindo assim que qualquer máquina na rede acesse o compartilhamento. Isso é feito usando um curinga no arquivo de configuração do NFS. No entanto, esteja ciente de que essa abordagem pode ter implicações significativas para a segurança da sua rede, pois permite que qualquer um com acesso à rede monte e acesse o diretório compartilhado. É altamente recomendado restringir o acesso apenas a hosts confiáveis ou redes confiáveis.

### No Servidor (por exemplo, Kali Linux)

1. **Edite o arquivo de exportação:** Abra o arquivo `/etc/exports` em um editor de texto com permissões de root.
    
    Você pode usar o caractere curinga `*` (asterisco) para indicar que qualquer host pode acessar o compartilhamento, ou usar sub-redes para limitar o acesso a uma faixa específica de endereços IP na sua rede.
    
    Para permitir o acesso a qualquer host:
    
    bash
    

`/caminho/do/diretorio *(rw,sync,no_subtree_check)`

Ou, para permitir acesso apenas a uma sub-rede específica (por exemplo, 192.168.1.0/24):

- `/caminho/do/diretorio 192.168.1.0/24(rw,sync,no_subtree_check)`
    
    **Nota:** Substitua `/caminho/do/diretorio` pelo caminho do diretório que você deseja compartilhar.
    
- **Aplique as mudanças:** Depois de salvar o arquivo `/etc/exports`, aplique as mudanças com:
    
    sh
    
- `sudo exportfs -arv`
    
- **Reinicie o serviço NFS** para garantir que as novas configurações sejam aplicadas.
    
    sh
    

1. `sudo systemctl restart nfs-kernel-server`
    

### No Cliente (por exemplo, Arch Linux)

Para montar o diretório compartilhado em um cliente, siga os mesmos passos descritos anteriormente, substituindo `ip_do_servidor` pelo endereço IP do servidor NFS ou pelo nome de domínio, se disponível e resolvível.

### Considerações de Segurança

- **Restrições de Acesso:** Mesmo quando não se especifica um host, é possível e recomendado restringir o acesso por meio de firewalls ou ajustes de rede para limitar quais máquinas podem se conectar ao servidor NFS.
- **Uso de Curingas e Sub-redes:** Se possível, limite o acesso a sub-redes específicas ao invés de usar o curinga `*`, para reduzir o risco de acesso não autorizado.
- **Verificações Adicionais:** Certifique-se de realizar verificações de segurança regulares e monitoramento de rede para identificar e mitigar possíveis ameaças.

Lembre-se de que, ao configurar serviços de rede como o NFS, entender e aplicar as melhores práticas de segurança é crucial para proteger seus dados e sistemas.