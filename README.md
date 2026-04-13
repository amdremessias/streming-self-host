Estrutura de Pastas Recomendada: Para que tudo funcione perfeitamente, recomendo organizar sua pasta /docker/data assim:


/docker/data/torrents (Onde o qBittorrent baixa)

/docker/data/media/Filmes (Onde o Radarr organiza)

/docker/data/media/Series (Onde o Sonarr organizaria)



Prowlarr (Porta 9696): É aqui que você adiciona seus sites de Torrent (Indexers). Ele vai "empurrar" essas configurações automaticamente para o Radarr.



Radarr (Porta 7878): Aqui você adiciona os filmes que deseja. Ele vai perguntar ao Prowlarr onde encontrar, mandar o download para o qBittorrent e, quando terminar, ele move o arquivo para a pasta de Filmes do Jellyfin.



Próximos Passos na Interface Web:


No Prowlarr: Adicione seus indexers e em Settings > Apps, adicione o Radarr usando a API Key dele.

No Radarr: Em Settings > Download Clients, adicione o qBittorrent (o host será o nome do serviço: qbittorrent).

Ficou claro como eles se comunicam ou quer ajuda com a configuração inicial das APIs?

_______________________________________________________________________________________________________________________


O usuário padrão do qBittorrent (especificamente nesta imagem da LinuxServer que usamos no Docker) mudou recentemente por questões de segurança.

Aqui estão as credenciais:

Usuário: admin

Senha: É gerada aleatoriamente na primeira inicialização e exibida nos logs do container.

Como encontrar a senha:
Como você está usando Docker Compose, rode o seguinte comando no terminal:

Bash
docker logs qbittorrent
Procure por uma linha parecida com esta:
+---------------------------------------+
| Password: XXXXXXXX-XXXX-XXXX-XXXX |
+---------------------------------------+

Notas importantes:
Antigamente: A senha era adminadmin, mas a LinuxServer removeu essa opção para evitar que pessoas deixassem seus servidores expostos.

Mude Imediatamente: Assim que logar na interface Web (porta 8080), vá em Tools > Options > Web UI e altere o usuário e a senha para algo de sua preferência.

Segurança: Se você pretende acessar isso fora da sua rede local, não esqueça de trocar essa senha, pois o qBittorrent é um alvo comum de ataques se ficar com a senha padrão ou exposta.


______________________________________________________________________________________________________________________

