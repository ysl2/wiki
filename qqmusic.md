# qqmusic

## QQMusic cannot boot on linux

Append ` --no-sandbox %U` into `Exec`, like this:

```text
sudo vim /usr/share/applications/qqmusic.desktop

[Desktop Entry]
Name=qqmusic
Exec=/opt/qqmusic/qqmusic --no-sandbox %U
Terminal=false
Type=Application
Icon=qqmusic
StartupWMClass=qqmusic
Comment=Tencent QQMusic
Categories=AudioVideo;
```
