# docker

## Install docker

- By brew:

  ```bash
  brew install --cask docker
  ```

- By apt:

  ```bash
  sudo apt install -y docker.io
  ```

- By [colima](https://github.com/abiosoft/colima) (brew):

  ```bash
  brew install colima docker
  colima start

  # Start colima in background and enable it to start on login:
  brew services start colima  # Or: `colima start --background`
  ```

## Uninstall docker

- By brew:

  ```bash
  # Ref: https://github.com/docker/for-mac/issues/7046#issuecomment-2579215790
  brew uninstall --cask docker --force --verbose --debug
  brew uninstall --formula docker --force --verbose --debug
  ```

## Install docker plugins

- By brew:

  ```bash
  brew install docker-compose
  brew install docker-buildx
  ```

  For docker to find plugins, add `cliPluginsExtraDirs` to `~/.docker/config.json`:

  ```json
  {
    "cliPluginsExtraDirs": ["$HOMEBREW_PREFIX/lib/docker/cli-plugins"]
  }
  ```

- By source (docker-compose):

  ```bash
  # Ref: https://stackoverflow.com/a/79052312

  DOCKER_CONFIG=${DOCKER_CONFIG:-$HOME/.docker}
  mkdir -p $DOCKER_CONFIG/cli-plugins
  curl -SL "https://ghfast.top/https://github.com/docker/compose/releases/download/v2.33.0/docker-compose-$(uname -s)-$(uname -m)" -o $DOCKER_CONFIG/cli-plugins/docker-compose

  chmod +x $DOCKER_CONFIG/cli-plugins/docker-compose

  # test the installation with:
  docker compose version

  # expected output is: Docker Compose version v2.29.6
  ```

## Add user into docker group

```bash
sudo usermod -aG docker "$USER"
logout  # and login again
```

## Set Chinese mirror

```bash
sudo mkdir -p /etc/docker
sudo tee /etc/docker/daemon.json <<-'EOF'
{
    "registry-mirrors": ["https://docker.m.daocloud.io"]
}
EOF
sudo systemctl daemon-reload
sudo systemctl restart docker
```

## Check the host's IP in docker containers

```bash
ip route | awk '/default/ { print $3 }'
```

## Clean docker resources

```bash
docker system prune -a --volumes
```

WARNING! This will remove:

- all stopped containers
- all networks not used by at least one container
- all anonymous volumes not used by at least one container
- all images without at least one container associated to them
- all build cache
