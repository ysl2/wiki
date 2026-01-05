# [wm-sway] Localhost configs

`~/.vocal/0/scripts/wm/autostart_wayland.localhost.sh`

```bash
#!/bin/sh

fcitx5 -d -r
```

---

`~/.config/sway/autostart.localhost.sh`

```bash
#!/bin/sh

swaymsg output "*" bg /usr/share/backgrounds/Fuji_san_by_amaral.png fill
```
