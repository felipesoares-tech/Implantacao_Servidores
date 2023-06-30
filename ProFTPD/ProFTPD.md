# Tutorial ProFTPD

## Passo 1: Instalar o ProFTPD

Abra o terminal no seu sistema Linux.
Dependendo da distribuição Linux que você está usando, você pode usar o gerenciador de pacotes específico para instalar o ProFTPD. Por exemplo, no Ubuntu, você pode usar o seguinte comando:

```bash
sudo apt-get install proftpd
```

Siga as instruções na tela para concluir a instalação.

## Passo 2: Configurar o ProFTPD

Após a instalação, você precisará editar o arquivo de configuração do ProFTPD para personalizar as opções de acordo com suas necessidades. O arquivo de configuração está localizado em /etc/proftpd/proftpd.conf. Você pode editar o arquivo usando um editor de texto de sua preferência. Por exemplo:

Dentro do arquivo de configuração, você encontrará várias opções que podem ser ajustadas. Alguns dos parâmetros mais comuns são:

- ServerName: Define o nome do servidor FTP.
- ServerType: Especifica o modo de operação do servidor. O valor padrão é standalone, que é adequado para a maioria das configurações.
- DefaultRoot: Define o diretório raiz padrão para os usuários FTP.
- Port: Especifica a porta na qual o servidor FTP ouvirá. O valor padrão é 21.
- AllowUser: Permite especificar quais usuários do sistema têm permissão para se conectar ao servidor FTP.
- DenyUser: Permite especificar quais usuários do sistema têm permissão negada para se conectar ao servidor FTP.
- MaxInstances: Define o número máximo de conexões simultâneas permitidas.

Após fazer as alterações necessárias no arquivo de configuração, salve e feche o editor de texto.

## Passo 3: Reiniciar o serviço ProFTPD

Após fazer as alterações de configuração, você precisará reiniciar o serviço ProFTPD para que as alterações entrem em vigor. Use o seguinte comando para reiniciar o serviço:

```bash
sudo service proftpd restart
```

## Passo 4: Testar a conexão FTP

- Agora você pode testar a conexão FTP para ver se o servidor está funcionando corretamente. Você pode usar um cliente FTP, como o FileZilla, para se conectar ao servidor usando o endereço IP do servidor, a porta e as credenciais de um usuário válido.

- Certifique-se de permitir o acesso ao servidor FTP através do firewall do seu sistema, abrindo a porta especificada no arquivo de configuração do ProFTPD.