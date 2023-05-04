# Instalando o Servidor MariaDB no Debian 10
Você pode instalar o pacote do servidor MariaDB a partir dos repositórios oficiais do Debian executando o seguinte comando, que instalará o servidor MariaDB, cliente e todas as suas dependências.

```bash
$ apt install mariadb-server
```

É uma prática comum no Debian e seus derivados, como o Ubuntu, iniciar e habilitar daemons automaticamente por meio do systemd, imediatamente após serem instalados. O mesmo se aplica ao serviço MariaDB.

Você pode verificar se o serviço MariaDB está instalado e funcionando usando o seguinte comando systemctl.

```bash
$ systemctl status mariadb  
```