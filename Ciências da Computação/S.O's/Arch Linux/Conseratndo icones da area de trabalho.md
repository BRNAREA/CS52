primeiro va ate a pasta `/usr/share/icons/hicolor/scalable/apps` e verifique se todos os icones estao presentes , caso nao esteja todos os icones , baixe ou peca para alguem te envia-los novamente

depois de repor todos os icones rode o comando

`sudo gtk-update-icon-cache` passando o caminho da pasta `hicolor`
Ex:
`sudo gtk-update-icon-cache /usr/share/icons/hicolor`

Depois atualize o banco de dados do computador

`sudo update-desktop-database`

e reinicie a maquina

`reboot`




