# CLI TUI GUI tools

> Ref: <https://github.com/johnalanwoods/maintained-modern-unix>

| Basic Tool Name | Type (CLI/TUI/GUI) | Note                         | Link                                           |
| --------------- | ------------------ | ---------------------------- | ---------------------------------------------- |
| `nmtui`         | TUI                | Network                      | <https://man.archlinux.org/man/nmtui.1>        |
| `brightnessctl` | CLI                | Brightness                   | <https://github.com/Hummer12007/brightnessctl> |
| `redshift`      | CLI                | Brightness                   | <https://github.com/jonls/redshift>            |
| `bluetuith`     | TUI                | Bluetooth                    | <https://github.com/bluetuith-org/bluetuith>   |
| `xrandr`        | CLI                | Monitor control              | <https://man.archlinux.org/man/xrandr.1>       |
| `arandr`        | GUI                | Monitor control              | <https://github.com/haad/arandr>               |
| `termscp`       | TUI                | SFTP in terminal             | <https://github.com/veeso/termscp>             |
| `nvtop`         | TUI                | Check GPU status in terminal | <https://github.com/Syllo/nvtop>               |
| `ncdu`          | TUI                | Check disk usage             | <https://man.archlinux.org/man/ncdu.1>         |
| `bottom`        | TUI                | Check system status          | <https://github.com/ClementTsang/bottom>       |
| `feh`           | TUI                | For desktop wallpaper        | <https://github.com/derf/feh>                  |
| `picom`         | TUI                | Window transparent           | <https://github.com/yshui/picom>               |
| `flameshot`     | GUI                | Image capture                | <https://github.com/flameshot-org/flameshot>   |
| `dunst`         | CLI                | Show notification            | <https://github.com/dunst-project/dunst>       |
| `udiskie`       | GUI                | USB mount                    | <https://github.com/coldfix/udiskie>           |
| `tlp`           | CLI                | Power saver                  | <https://github.com/linrunner/TLP>             |
| `lxappearance`  | GUI                | GTK theme changer            | <https://github.com/lxde/lxappearance>         |

| Other Tool Name | Type (CLI/TUI/GUI) | Note                             | Link                                                |
| --------------- | ------------------ | -------------------------------- | --------------------------------------------------- |
| `bluetoothctl`  | CLI                | Bluetooth                        | <https://man.archlinux.org/man/bluetoothctl.1>      |
| `img2pdf`       | CLI                | Image to PDF, for Latex          | <https://github.com/josch/img2pdf>                  |
| `pdf2svg`       | CLI                | PDF to SVG, for Typst            | <https://github.com/dawbarton/pdf2svg>              |
| `qrcp`          | CLI                | File transfer                    | <https://github.com/claudiodangelis/qrcp>           |
| `carbonyl`      | TUI                | Browser in terminal              | <https://github.com/fathyb/carbonyl>                |
| `surf`          | GUI                | Lightweight browser              | <https://surf.suckless.org/>                        |
| `trans`         | CLI                | Language translate               | <https://github.com/soimort/translate-shell>        |
| `htop`          | TUI                | Check system status              | <https://github.com/htop-dev/htop>                  |
| `crlf2lf`       | CLI                | Change file ending               | <https://github.com/XadillaX/node-crlf2lf>          |
| `zathura`       | GUI                | PDF Viewer                       | <https://github.com/pwmt/zathura>                   |
| `chafa`         | CLI                | Terminal image renderer          | <https://github.com/hpjansson/chafa>                |
| `tldraw`        | GUI                | Whiteboard                       | <https://github.com/tldraw/tldraw>                  |
| `wechat`        | GUI                | WeChat (with unofficial flatpak) | <https://github.com/web1n/wechat-universal-flatpak> |
| `qq`            | GUI                | Official QQ                      | <https://im.qq.com/linuxqq/index.shtml>             |
| `gh`            | CLI                | Official Github CLI              | <https://github.com/cli/cli>                        |
| `gh-dash`       | TUI                | github dashboard                 | <https://github.com/dlvhdr/gh-dash>                 |
| `color-picker`  | GUI                | Color picker                     | <https://github.com/keshavbhatt/ColorPicker>        |
| `mycli`         | CLI                | mysql                            | <https://github.com/dbcli/mycli>                    |
| `go-grip`       | CLI                | markdown previewer               | <https://github.com/chrishrb/go-grip>               |

## Brightness

```bash
#  Increase by 3%
brightnessctl set 3%+

# decrease by 3%
brightnessctl set 3%-
```

## redshift

```bash
# install
sudo apt install redshift
# Set to default night mode colur
redshift -P -O 4500K
# Reset
redshift -x
```

## Bluetooth: bluetoothctl

```
要使用 bluetoothctl 连接蓝牙设备，您可以按照以下步骤进行操作：

打开终端并输入 bluetoothctl 进入蓝牙控制台。

输入 power on，确保蓝牙适配器已经开启。

输入 agent on，启用默认的蓝牙代理。

输入 scan on，开始扫描周围的蓝牙设备。等待一段时间，直到您看到要连接的设备的 MAC 地址。

输入 pair <device MAC>，将 <device MAC> 替换为您要连接的设备的 MAC 地址。这将发起配对过程。

如果需要输入配对码，按照提示进行操作。配对码通常会在蓝牙设备上显示或者在设备的用户手册中提供。

输入 trust <device MAC>，将设备标记为受信任的设备，以便将来自动连接。

输入 connect <device MAC>，将 <device MAC> 替换为您要连接的设备的 MAC 地址。这将尝试建立与设备的连接。

如果连接成功，您应该会在终端中看到一条消息确认连接成功。

请注意，上述步骤中的 <device MAC> 是要连接的蓝牙设备的 MAC 地址。您可以在扫描步骤中获取它。此外，根据设备的类型和要求，可能还需要进行其他步骤。如果您遇到任何问题，请参考蓝牙设备的用户手册或官方文档，以获取更详细的指导。
```

## Convert image format

img -> pdf

```bash
pip install img2pdf

img2pdf *.jpg -o output.pdf
```

pdf -> svg

```bash
sudo apt install pdf2svg
```

## Audio: alsamixer

For headphone settings:

<img src="assets/[common]-CLI-TUI-GUI-tools/img/2025-07-13-11-44-36.png" alt="" width=100%>

Or amixer

```bash
amixer -M get Master
amixer -M set Master 0%
amixer -M set Master 5%+
```
