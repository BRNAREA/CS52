#           Pipelining HTTP
__O pipelining HTTP__ é um recurso do HTTP / 1.1 que permite várias solicitações HTTP sejam enviadas em uma única conexão TCP [[Protocolo TCP]] sem esperar pelas respostas correspondentes . A especificação  HTTP / 1.1 requer que os servidores respondam às solicitações em pipeline corretamente , enviando de volta respostas não pipeline , mas válidas , mesmo se o servidor não suportar o pipelining HTTP. Apesar desse requisito , muitos servidores HTTP / 1.1  legados não suportam o pipelining corretamente , forçando a maioria dos clientes HTTP a não usar o pipelining HTTP na prática.

A técnica foi substituida pela multiplexação via HTTP / 2 , que é suportada pela maioria dos navegadores modernos. 

![[Pasted image 20220712154131.png]]
