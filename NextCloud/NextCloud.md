# NextCloud

## Pré-requisitos

![requisitos](/NextCloud//assets/img/requisitos.png)

## Instale Apache, MariaDB e PHP

[1. Instalação php](/NextCloud/PHP/php.md)

[2. Instalação apache](/NextCloud//APACHE/apache.md)

Depois que todos os pacotes estiverem instalados, abra o arquivo php.ini e ajuste algumas configurações recomendadas:

```bash
$ nano /etc/php/8.1/apache2/php.ini
```

Altere as seguintes configurações:

```bash
memory_limit = 512M
upload_max_filesize = 500M
post_max_size = 500M
max_execution_time = 300
date.timezone = Ásia / Calcutá
```

Salve e feche o arquivo quando terminar. Em seguida, inicie o serviço Apache e MariaDB e permita que eles iniciem após a reinicialização do sistema com o seguinte comando:

```bash
systemctl start apache2 
systemctl start mariadb 
systemctl enable apache2 
systemctl enable mariadb
```

## Configurar banco de dados para NextCloud

Em seguida, você precisará criar um banco de dados e um usuário de banco de dados para o NextCloud. Para fazer isso, efetue login no shell do MariaDB com o seguinte comando:
```bash
$ mysql -u root -p
```

Forneça sua senha root quando solicitado e crie um banco de dados e um usuário com o seguinte comando:

```bash
MariaDB [(none)]> CREATE DATABASE nextclouddb; 
MariaDB [(none)]> CREATE USER 'nextclouduser'@'localhost' IDENTIFIED BY 'password';
```

Em seguida, conceda todos os privilégios ao nextclouddb com o seguinte comando:

```bash
MariaDB [(none)]> GRANT ALL ON nextclouddb.* TO 'nextclouduser'@'localhost';
```

Quando terminar, você pode prosseguir para a próxima etapa.

## Baixar NextCloud

Primeiro, visite a página de download do NextCloud e baixe a versão mais recente do NextCloud no seu sistema. No momento da redação deste artigo, a versão mais recente do NextCloud é 26.0.1. Você pode baixá-lo com o seguinte comando:

```bash
$ wget https://download.nextcloud.com/server/releases/nextcloud-26.0.1.zip
```
Após a conclusão do download, descompacte o arquivo baixado com o seguinte comando:
```bash
$ unzip nextcloud-26.0.1.zip
```

Em seguida, mova o diretório extraído para o diretório raiz da web do Apache:
```bash
$ mv nextcloud /var/www/html/
```
Em seguida, atribua permissões apropriadas ao diretório nextcloud com o seguinte comando
```bash
chown -R www-data:www-data /var/www/html/nextcloud/ 
chmod -R 755 /var/www/html/nextcloud/
```
Quando terminar, você pode prosseguir para a próxima etapa.

## Configurar o Apache para NextCloud

Em seguida, você precisará criar um arquivo de configuração de host virtual do Apache para servir o NextCloud. Você pode criá-lo com o seguinte comando:

```bash
$ nano /etc/apache2/sites-available/nextcloud.conf
```

Adicione as seguintes linhas:
```bash
<VirtualHost *:80>
     ServerAdmin admin@example.com
     DocumentRoot /var/www/html/nextcloud/
     ServerName ipdamaquina

     Alias /nextcloud "/var/www/html/nextcloud/"

     <Directory /var/www/html/nextcloud/>
        Options +FollowSymlinks
        AllowOverride All
        Require all granted
          <IfModule mod_dav.c>
            Dav off
          </IfModule>
        SetEnv HOME /var/www/html/nextcloud
        SetEnv HTTP_HOME /var/www/html/nextcloud
     </Directory>

     ErrorLog ${APACHE_LOG_DIR}/error.log
     CustomLog ${APACHE_LOG_DIR}/access.log combined

</VirtualHost>
```

Salve e feche o arquivo quando terminar. Em seguida, ative o arquivo do host virtual Apache e outros módulos necessários usando os seguintes comandos:

```bash
a2ensite nextcloud.conf 
a2enmod rewrite 
a2enmod headers 
a2enmod env 
a2enmod dir 
a2enmod mime
```

Por fim, reinicie o serviço Apache para aplicar a nova configuração:

```bash
systemctl restart apache2
```

