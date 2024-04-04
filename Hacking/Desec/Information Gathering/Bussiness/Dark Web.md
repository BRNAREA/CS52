Base de Leaks na DW:

- http://pwndb2am4tzkvold.onion/ 

## Navegadores

- Tor browser
- Firefox
	sudo apt install tor proxychains
	sudo nano /etc/proxychains.conf
		sudo service tor start
		dynamic_chain
		socks5 127.0.0.1 9050
			Network settings on firefox:
			Manual configuration:
				SOCKS HOST 127.0.0.1 PORT 9050 AND ENABLE SOCKSV5
				No proxy for localhost, 127.0.0.1
				Enable Proxy DNS when using SOCKS v5



