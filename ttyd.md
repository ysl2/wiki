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
./ssl.sh
```

## Usage

```bash
ttyd -S -C server.crt -K server.key -c "$YOUR_USERNAME":"$YOUR_PASSWORD" -p 36011 -w ~ -W -t fontSize=17 -t fontFamily="FiraCode" -t disableLeaveAlert=true -t disableResizeOverlay=true -t enableZmodem=true -t enableTrzsz=true -t enableSixel=true -t 'theme={"foreground": "#cdd6f4", "background": "#1e1e2e", "cursor": "#f5e0dc", "black": "#45475a", "red": "#f38ba8", "green": "#a6e3a1", "yellow": "#f9e2af", "blue": "#89b4fa", "magenta": "#f5c2e7", "cyan": "#94e2d5", "white": "#bac2de", "brightBlack": "#585b70", "brightRed": "#f38ba8", "brightGreen": "#a6e3a1", "brightYellow": "#f9e2af", "brightBlue": "#89b4fa", "brightMagenta": "#f5c2e7", "brightCyan": "#94e2d5", "brightWhite": "#a6adc8"}' "$SHELL" &; disown

autossh -M 37011 -NfR 47.xxx.xxx.227:38011:localhost:36011 -p 36000 gongwang@47.xxx.xxx.227
```
