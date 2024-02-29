Suponha que temos uma função que calcula o fatorial de um número inteiro. Essa função pode ser escrita da seguinte forma:

javascriptCopy code

`function fatorial(n) {   if (n <= 1) {     return 1;   } else {     return n * fatorial(n - 1);   } }`

Essa implementação é simples e funciona corretamente, mas pode ser bastante ineficiente para números grandes, pois a função é chamada diversas vezes com os mesmos argumentos.

Podemos aplicar a técnica de memoização para evitar o cálculo repetido do fatorial de um mesmo número. Aqui está uma nova implementação usando a memoização:

```js
function memoizedFatorial() {   
	const cache = {};
	
	function fatorial(n) {     
		if (n <= 1) {       
			return 1;     
		} else if (n in cache) {       
			console.log("Retornando resultado memoizado...");     
			return cache[n];     
		} else {       
			console.log("Calculando resultado...");       
			const result = n * fatorial(n - 1);       
			cache[n] = result;
			return result;    
		 }   
	}    
	return fatorial; 
}  
const fatorial = memoizedFatorial(); 
console.log(fatorial(5)); // Calculando resultado... 120 console.log(fatorial(5)); // Retornando resultado memoizado... 120 
console.log(fatorial(7)); // Calculando resultado... 5040 console.log(fatorial(7)); // Retornando resultado memoizado... 5040 
```


Nesta nova implementação, primeiro criamos a função `memoizedFatorial` que retorna uma closure (função interna) que recebe um único argumento `n`, o número inteiro para o qual queremos calcular o fatorial.

Dentro dessa closure, criamos um objeto `cache` vazio que será usado para armazenar os resultados da função. Em seguida, verificamos se o fatorial de `n` já está armazenado no cache. Se sim, retornamos o valor correspondente sem executar todo o código da função novamente. Se não, calculamos o fatorial normalmente e armazenamos o resultado no objeto `cache`, antes de retorná-lo.

Para utilizar a função `fatorial`, primeiro a armazenamos em uma variável `fatorial`, chamando a função `memoizedFatorial` sem passar nenhum argumento. Em seguida, podemos chamar a função `fatorial` passando o argumento `n` desejado.

Ao chamar a função `fatorial` duas vezes com o mesmo argumento `n`, podemos ver que a segunda chamada retorna o valor memoizado sem executar novamente todo o código da funçãoi
