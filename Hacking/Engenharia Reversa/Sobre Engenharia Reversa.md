## O que é a Engenharia Reversa ?

A Engenharia Reversa é o processo de entender como funciona uma execução de um programa sem ter acesso ao código fonte do programa.

- Análise de malware
- Reimplementação de software e protocolos
- Correção de bugs.
- Análise de vulnerabilidade
- Adição/Alteração de recursos no Software
- Proteção Anti-Pirataria
- Alugns termos e abreviações para engenharia reversa incluem: RCE (Reverse Code Engineering), RE, e reversing.

No seguinte código feito em C vamos analisar e pensar como a RCE funciona por tras dos programas

```C
#include <stdio.h>

int main() 
{
	 ;printf("a");
	 	return 0;
}
```

No codigo acima incluimos a biblioteca stdio.h a padrao de C , quando executamos o programa "ldd" em cima do nosso programa "ldd main.c" ele retorna quais bibliotecas este programa , mas quem de fato escreve é o KERNEL do sistema, vejamos o desenho abaixo

![[Sobre Engenharia Reversa 2024-02-20 18.07.23.excalidraw]]