# Instalação php

>1. Adicione a chave do repositório.
```bash
$ wget -qO - https://packages.sury.org/php/apt.gpg | sudo apt-key add -
```

>2. Adicione o repositório.
```bash
$ echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" | sudo tee /etc/apt/sources.list.d/sury-php.list
```

>3. Atualize o índice do pacote.
```bash
$ sudo apt update
```

>4. Instale o PHP 8.0 do repositório deb.sury.org.
```bash
$ sudo apt install php8.0
```
>5. Verifique a instalação do PHP 8.
```bash
$ php -v
```