# Tutorial SCP

Passo 1: Verifique se o servidor SSH está instalado

Antes de usar o scp, verifique se o servidor SSH está instalado no servidor remoto, conforme explicado no passo 1 do tutorial anterior.

Passo 2: Copiar um arquivo do servidor local para o servidor remoto

No terminal do seu sistema local, use o seguinte comando scp para copiar um arquivo do seu sistema local para o servidor remoto:

```bash
scp caminho_do_arquivo usuário@servidor_remoto:caminho_destino
```
Substitua "caminho_do_arquivo" pelo caminho completo do arquivo que você deseja copiar. Em seguida, substitua "usuário" pelo nome de usuário correto no servidor remoto e "servidor_remoto" pelo endereço IP ou nome de domínio do servidor remoto. Por fim, substitua "caminho_destino" pelo caminho no servidor remoto onde você deseja salvar o arquivo.