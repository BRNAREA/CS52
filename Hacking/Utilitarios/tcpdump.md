```ad-info
TYPE: NETWORK ANALYSER

tcpdump faz a mesma coisa que o wireshark so que em CLI, voce consegue monitorar sua rede atraves do terminal.
```

```ad-question
title: MODO DE USO

**tcpdump -v -r arp.pcap**
```

```sh
tcpdump -ver arp.pcap
tcpdumo -vr arp.pcap

tcpdump -v -i eth0 icmp -w icmp.pcap
```

- -v=verbose
- -i=interface
- -w=write nome.pcap
- -r=read
- -numeric
- -e=ethernet
- -A=ASCII
- -X=hexadecimal

```sh
tcpdump -vnr portscanlog.pcap src host <IP> | cut -d "," -f 1 | egrep -v "tos|S" | grep "F\."
```