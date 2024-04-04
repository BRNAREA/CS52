<h1 align="center">Estudo Tecnico</h1>


<h2 align="center">Senhas em sistemas Linux</h2>
<hr>

A primeira coisa que a gente poderia fazer ao ter acesso administrativo do sistema seria obter as contas de usuarios e as hashes de senhas para tentar quebra-las e obter elas em texto claro.

Com isso poderiamos utilizar em outras partes do sistema.

```ad-question
title: como funciona o sistema de hashes no linux?
Pra isso precisamos voltar um pouco no tempo , la nas primeiras versoes de linux era utilizado o arquivo /etc/passwd onde este arquivo era usado para armazenar as senhas do linux mas hoje este arquivo virou somente para as informacoes basicas , como : nome do usuario, modo de encrypt, id do usuario, o caminho onde fica o diretorio do usuario e o shell

mas antigamente para visualizar esse arquivo nao precisava de autorizacao do super usuario e isso o tornava facil de pegar os hashes de senhas de outros usuarios e tentar quebra-las facilmente.

O linux viu isso como um problema de seguranca e trocou o formato de armazenamento utilizando o arquivo `shadow`. /etc/shadow

Uma vez que pegamos os hashes em /etc/shadow poderiamos tentar quebrar esse hashes e obter a senhas dos usuarios

```

<h5 align="center">Entendendo a estrutura do shadow</h5>
<hr>

Vemos que nesse arquivo shadow pode parecer um pouco complicado , mas observe atentamente que ha um padrao.

```sh
root:$y$j9T$19d35hGBhyVcN7uoAZ/aQ.$X5YEHdbBegV2E41tBh7TpL71AWzTxcK.3M.LZigWtz3:19783::::::
bin:!*:19783::::::
daemon:!*:19783::::::
mail:!*:19783::::::
ftp:!*:19783::::::
http:!*:19783::::::
nobody:!*:19783::::::
dbus:!*:19783::::::
systemd-coredump:!*:19783::::::
systemd-network:!*:19783::::::
systemd-oom:!*:19783::::::
systemd-journal-remote:!*:19783::::::
systemd-resolve:!*:19783::::::
systemd-timesync:!*:19783::::::
tss:!*:19783::::::
uuidd:!*:19783::::::
polkitd:!*:19783::::::
spectrall:$y$j9T$OfNnOJsacFXkmKRiefy7R/$mQc8vKT/eDWnWLatNC7Vv82MZpYb3jyN.6Q7vivRG34:19783:0:99999:7:::
avahi:!*:19783::::::
git:!*:19783::::::
geoclue:!*:19790::::::
rtkit:!*:19790::::::
sddm:!*:19790::::::
usbmux:!*:19790::::::
flatpak:!*:19790::::::
dhcpcd:!*:19792::::::
libvirt-qemu:!*:19792::::::
qemu:!*:19792::::::
dnsmasq:!*:19792::::::
brltty:!*:19792::::::
gluster:!*:19792::::::
rpc:!*:19792::::::
_talkd:!*:19801::::::
ntp:!*:19801::::::
desec:$y$j9T$rMu8WD/y2108C/ne2O3aa0$rAHBHFvJ/TH3.eoRsnIFc2Dx4ezF0c3a/kl68UpoNo0:19801:0:99999:7:::
named:!*:19803::::::
nvidia-persistenced:!*:19806::::::
saned:!*:19806::::::
dovenull:!*:19808::::::
dovecot:!*:19808::::::
rpcuser:!*:19809::::::
mysql:!*:19809::::::
snort:!:19809:0:99999:7:::
ldap:!*:19809::::::
postgres:!*:19809::::::
redis:!*:19809::::::
```

Este padrao segue de um $ (cifrao) seguido de uma string aleatorio ate um outro $ (cifrao) seguido de outra string aleatorio , ate um outro $ (cifrao) seguido de mais um string aleatoria ate os : (dois pontos).

Isso forma a senha encriptada do usuario
Mas como que o Linux faz isso?

Ele faz isso atraves de uma funcao <mark style='background:var(--mk-color-red)'>crypt()</mark> se analisarmos o manual oficial dessa funcao , ele exibe uma tabelinha que diz corretamente como funciona , na tabela diz:

```ad-cite
A primeira informacao ou seja o primeiro $(cifrao) significa o id de encrypt
A segunda informacao significa o salt
E a terceira a senha de fato encriptada.
```


| ID  | Method                                          |
| --- | ----------------------------------------------- |
| 1   | MD5                                             |
| 2a  | Blowfish (not in mainline glibc; added in some) |
| 5   | SHA-256                                         |
| 6   | SHA-512                                         |

```ad-question
title: SALT

O salt eh o mecanismo de protecao do hash, ele pega uma porcao de dados aleatorios e adicona ao hash, isso para que nem todas as senhas iguais tenham o mesmo resultado na hora de encrypta-las .

O salt (essa porcao de codigo adiconal) antes de gerar a funcao <mark style='background:var(--mk-color-red)'>crypt()</mark> do linux, faz com que o hash dos usuarios com fiquem completamente diferente , independente se esses usuarios tenham a mesma senha. 

A gente pode gerar atraves do `openssl` por exemplo  uma senha com `salt` usando os mesmos padroes de encryptacao do linux.

```

Gerando senha com salt:

```sh
openssl passwd -6 -salt wallace 123
$6$wallace$YFPCV5.8QDxRdE28OICReMLMxuzNOTXJjZZBY7rpctmM1UQtZBKoEi4BypGRZGhpFWk5.QUDVLkkOFnb0yva0.
```
Com o mando acima vai gerar uma senha com SHA-512 com um SALT aplicado.

Agora vamos pegar o mesmo salt por exemplo de um usuario teste :

```
teste:$y$j9T$rMu8WD/y2108C/ne2O3aa0$rAHBHFvJ/TH3.eoRsnIFc2Dx4ezF0c3a/kl68UpoNo0:19801:0:99999:7:::

openssl passwd -6 salt rMu8WD/y2108C/ne2O3aa0 123
```

Eles terao a mesma senha encriptada , porque usamos o mesmo salt.

- Hashes.com
- md5decrypt.net