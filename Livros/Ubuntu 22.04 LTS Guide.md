O `gerenciador de pacote pacman`  é um dos maiores recursos do Arch Linux. Ele combina um simples pacote binario com um `sistema de construcao` de facil uso.

---

_1_ Uso
Um pacote é um arquivo que contém:
- Todos os arquivos (compilados) de uma aplicação.
- metadados sobre a aplicação , como o nome da aplicação , versão , depedencias , etc..
- arquivos de instalação e diretivas para _pacman_ 
- (opcional) arquivos extras para fazer sua vida mais facil , como um start/stop script.

Usando o gerenciador de pacote _pacman_ voce pode instalar , atualizar e remover esses pacotes. 

Usar pacotes ao inves de compilar e instalar programas por si mesmos tem varios beneficios :

- Facilmente atualizavel: _pacman_ vai atualizar pacotes existentes o mais breve possivel .
- Checks de Depedencias : _pacman_ controla depedencias para voce , voce apenas precisa especificar ao programa e o _pacman_ instalara junto com todos os outros programas necessarios.
- Remocao limpa : _pacman_ tem uma lista de cada arquivo em um pacote; dessa maneira . nenhum arquvo e intencionalmente retirado quando voce decide remover um pacote


```

mv macOSBigSur ~/.icons                     # install as local
sudo mv macOSBigSur /usr/share/icons        # install as root
```

  
  
**Linux Uninstall**  

```

rm -r ~/.icons/macOSBigSur                  www# remove from local
sudo rm -r /usr/share/icons/macOSBigSur   


org.gnome.ArchieveManager
````


### Removing unused packages (orphans)

Orphans are packages that were installed as a dependency and are no longer required by any package.

They can accumulate on your system over time either due to uninstalling packages using `pacman -R _package_` instead of `pacman -Rs _package_`, installing packages as [makedepends](https://wiki.archlinux.org/title/Makedepends "Makedepends"), or packages removing dependencies in newer versions.

For recursively removing orphans and their configuration files:

# pacman -Qtdq | pacman -Rns -

```
npx create-html5-boilerplate new-site
cd new-site
npm install
npm start
```