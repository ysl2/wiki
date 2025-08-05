# ttyd

## Install

> Ref:
>
> - <https://github.com/tsl0922/ttyd>
> - <https://github.com/metorm/ttyd-nerd-font>

```bash
sudo apt-get update
sudo apt-get install -y build-essential cmake git libjson-c-dev libwebsockets-dev
git clone git@github.com:ysl2/ttyd.git
cd ttyd && mkdir build && cd build
cmake ..
make && sudo make install
```

## Usage

```bash
ttyd -c "$YOUR_USERNAME":"$YOUR_PASSWORD" -p 36011 -W -t fontSize=18 -t fontFamily="FiraCode" -t disableLeaveAlert=true -t disableResizeOverlay=true -t enableZmodem=true -t enableTrzsz=true -t enableSixel=true tmux new-session -A -s main zsh &; disown
autossh -M 37011 -NfR 47.xxx.xxx.227:38011:localhost:36011 -p 36000 yusongli@47.xxx.xxx.227
```
