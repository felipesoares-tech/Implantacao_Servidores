# Net-Tools

O net-tools e o iproute são duas ferramentas úteis para gerenciamento de redes no sistema Linux. Neste tutorial, você aprenderá como usar essas ferramentas para uma melhor gestão da sua rede.

1 - Instalando o net-tools e iproute

A maioria das distribuições Linux já inclui o net-tools e o iproute no pacote de instalação por padrão. Caso contrário, você pode usar o gerenciador de pacotes da sua distribuição para instalá-los.

Para instalar o net-tools no Debian e Ubuntu, você pode usar o comando abaixo:

```bash
felipe@notebook-550XDA:~$ sudo apt install net-tools
```

Para instalar o iproute no Debian e Ubuntu, você pode usar o comando abaixo:

```bash
felipe@notebook-550XDA:~$ sudo apt install iproute2
```

2 - Usando o net-tools

O net-tools inclui ferramentas como ifconfig, arp, netstat e route. Abaixo estão alguns exemplos de como usar essas ferramentas:

ifconfig - exibe informações sobre as interfaces de rede, incluindo endereços IP
```bash
root@notebook-550XDA:/home/felipe# ifconfig
enp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.24.46  netmask 255.255.255.192  broadcast 192.168.24.63
        inet6 fe80::a288:9f48:98:1dbf  prefixlen 64  scopeid 0x20<link>
        ether 8c:b0:e9:34:df:1f  txqueuelen 1000  (Ethernet)
        RX packets 52386  bytes 62216237 (62.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 23451  bytes 7303014 (7.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Loopback Local)
        RX packets 1577  bytes 157667 (157.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1577  bytes 157667 (157.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlo1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 172.16.1.147  netmask 255.255.252.0  broadcast 172.16.3.255
        inet6 fe80::bfe:5a2e:cdd2:923e  prefixlen 64  scopeid 0x20<link>
        ether 0c:9a:3c:06:5c:20  txqueuelen 1000  (Ethernet)
        RX packets 24718  bytes 4176468 (4.1 MB)
        RX errors 0  dropped 2069  overruns 0  frame 0
        TX packets 2410  bytes 471157 (471.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```
arp -a - exibe a tabela ARP (tradução de endereços de hardware para endereços IP)

```bash
root@notebook-550XDA:/home/felipe# arp -a
_gateway (192.168.24.62) em 70:4c:a5:68:57:f1 [ether] em enp2s0
? (172.16.0.40) em d2:b1:a6:63:73:78 [ether] em wlo1
_gateway (172.16.3.254) em 70:4c:a5:68:57:f8 [ether] em wlo1
```
