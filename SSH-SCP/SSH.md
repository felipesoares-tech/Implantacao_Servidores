# Tutorial SSH

## Introdução


Uma ferramenta essencial para se ter domínio na administração de sistemas é o SSH.

O SSH, ou Secure Shell , é um protocolo usado para fazer login em sistemas remotos de forma segura. É a maneira mais comum de acessar servidores remotos Linux.

Neste guia, vamos discutir como usar o SSH para se conectar a um sistema remoto.

## Sintaxe básico

Para se conectar a um sistema remoto usando o SSH, vamos usar o comando ssh. A forma mais básica do comando é:

```bash
ssh remote_host
```
Este remote_hostexemplo é o endereço IP ou o nome de domínio ao qual você está tentando se conectar.

Este comando assume que o nome de usuário no sistema remoto é o mesmo que o seu nome de usuário em seu sistema local.

Se o nome de usuário for diferente no sistema remoto, especifique isso usando esta sintaxe:

```bash
ssh remote_username@remote_host
```
Depois de se conectar ao servidor, será solicitado que verifique sua identidade fornecendo uma senha. Mais tarde, vamos mostrar como gerar chaves para usar em vez de senhas.

Para sair da sessão ssh e retornar em sua sessão de shell local, digite:
```bash
exit
```
