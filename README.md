Resumo da "Mágica":
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
