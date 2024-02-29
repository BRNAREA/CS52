Softwares packers são uma maneira de comprimir um executavel e combinar dados comprimidos com a descompressão de codigo em um unico executavel.

Esses packers são comumente usado por malwares para esconder sua presença de anti-virus scan e tambem para dificultar tarefas analiticas de engenharia reversa de arquivos packers.

Qualquer pessoa com um entendimento minimo em engenharia reversa pode facilmente fazer o unpack
de um programa na qual foi usado o upx.

Existem duas maneiras de fazer o **UNPACK** de um programa vamos ver os dois casos.

Primeiro precisamos de algumas ferramentas para nos ajudar no processo.

Sempre use uma maquina virtual.

As ferramentas que voce deve utilizar são as seguintes:

1) UPX Packer
2) DIE (Detect It Easy) ou PEID (Packer Detectors)
3) Um debugger como OllyDBG ou x64dbg
4) Scylla na qual é utilizado para reconstruir uma tabela importante se voce usar x64dbg já vem integrado !