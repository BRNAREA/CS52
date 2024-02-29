Métodos de análise de programas:

- Análise Estática : não executa o binário
	- Parsing (ex: pev)
	- Dessassembling (ex: IDA Pro)
- Análise Dinâmica: executa o binário
	- Sandbox (ex.: Cuckoo)
	- Debugger (ex.: gdb, x64dbg)
		- Execução concreta: limitações
		-  Cobertura de codigo
		- Atingibilidade