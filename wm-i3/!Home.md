# [wm-i3] Home

## Installation

### Build i3 and i3blocks from official source repo

```bash
# Build i3wm
sudo apt install libstartup-notification0-dev libxcb-xkb-dev libxcb-xinerama0-dev libxcb-randr0-dev libxcb-shape0-dev libxcb-util0-dev libxcb-cursor-dev libxcb-keysyms1-dev libxcb-icccm4-dev libxcb-xrm-dev libyajl-dev libev-dev libxkbcommon-x11-dev
cd ~/Documents/
git clone git@github.com:i3/i3.git
cd i3
rm -rf build
meson setup build
ninja -C build
sudo $(which ninja) -C build install
sudo mkdir -p /usr/share/xsessions
sudo ln -s /usr/local/share/xsessions/i3.desktop /usr/share/xsessions/i3.desktop

# Build i3blocks
sudo apt install automake autoconf
cd ~/Documents/
git clone git@github.com:vivien/i3blocks.git
cd i3blocks
./autogen.sh
./configure
make
sudo make install
```

### Install config file and it's dependencies

```bash
git clone git@github.com:ysl2/i3.git ~/.config/i3

pip install autotiling
cargo install i3-autolayout
sudo apt install xdotool rofi xcwd yad

# If using anaconda, you should `conda install -c conda-forge libstdcxx-ng`
# Ref: https://stackoverflow.com/a/75333466/13379393
# Disable this due to bug.
# git clone git@github.com/ysl2/i3expod-ng.git && cd i3expod-ng && make install
```

`config_bak` and `i3blocks.bak.conf` are the official config files, just for backup.

Log dir: `~/.vocal/.lock/i3`

## Disable DM and use startx to boot i3wm

```bash
# Disable DM, use starx to boot i3wm.
sudo systemctl set-default multi-user.target
# Enable DM, restore to default graphical desktop.
sudo systemctl set-default graphical.target
```

## Boost nautilus for i3wm

If you find nautilus is slow to open, you can try to remove xdg-desktop-portal packages:

```bash
systemctl --user mask xdg-desktop-portal-gnome xdg-desktop-portal-kde
killall xdg-desktop-portal xdg-desktop-portal-gnome xdg-desktop-portal-kde
systemctl --user status xdg-desktop-portal-gtk  # Check runnng status, if not start, use `systemctl --user start xdg-desktop-portal-gtk`
```
