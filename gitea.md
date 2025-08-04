# gitea

> [!NOTE]
> [assets/gitea](assets/gitea)

```bash
# If in Inner machine:
autossh -M 37001 -NfR 47.xxx.xxx.227:38001:localhost:36001 -p 36000 yusongli@47.xxx.xxx.227
autossh -M 37002 -NfR 47.xxx.xxx.227:38002:localhost:36002 -p 36000 yusongli@47.xxx.xxx.227
autossh -M 37003 -NfR 47.xxx.xxx.227:38003:localhost:36003 -p 36000 yusongli@47.xxx.xxx.227
vim docker-compose.yml
# Change `GITEA__server__SSH_PORT=36002` to `GITEA__server__SSH_PORT=38002`

# start
docker compose up -d

# stop and clean
docker compose down; docker rm -f $(docker ps | grep mysql | awk '{print $1}'); docker rm -f $(docker ps | grep gitea | grep com | awk '{print $1}'); docker volume rm gitea_gitea; docker network rm gitea_gitea; sudo sudo kill -9 $(ps aux | grep dockerd | grep -v grep | awk '{print $2}')

# WARNING: This will remove all data in the gitea container, including repositories and settings.
sudo rm -rf /mnt/nas/Public/gitea
```

```bash
# If in Inner machine, and push directly to local /mnt/nas/Public/gitea:
❯ git remote -v
gitea   ssh://git@localhost:36002/ysl2/repo.git (fetch)
gitea   ssh://git@localhost:36002/ysl2/repo.git (push)
```

| result | sshd  | inner | outer | SSH_PORT | SSH_LISTEN_PORT |
| ------ | ----- | ----- | ----- | -------- | --------------- |
| Y      | 22    | 22    | 222   | 222      | 222             |
| Y      | 22    | 22    | 35001 | 35001    | 35001           |
| Y      | 36000 | 22    | 35001 | 35001    | 35001           |
| Y      | 36000 | 22    | 35001 | 35001    | 22              |
| N      | 36000 | 22    | 35001 | 22       | 35001           |

| result | inner | outer | HTTP_PORT |
| ------ | ----- | ----- | --------- |
| Y      | 3000  | 3000  | 3000      |
| Y      | 3000  | 36001 | 3000      |
| N      | 3000  | 36001 | 36001     |
