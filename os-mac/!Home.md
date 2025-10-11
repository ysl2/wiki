# [os-mac] Home

> [!NOTE]
> [.assets/!Home](.assets/!Home)

## 网络设置与配置恢复

- Install sing-box from app store. <https://apps.apple.com/us/app/sing-box-vt/id6673731168>
- `xcode-select --install`
- 手动添加ssh的github 443端口配置
- 创建ssh keypair并添加到github
- git clone dotfiles和dotlinks -b mac，并执行恢复动作

## 依赖安装

```bash
/bin/bash -c "$(curl -fsSL https://ghfast.top/https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### 包列表

```bash
brew list -1 --installed-on-request > '/Users/songliyu/Documents/blog/os-mac/.assets/!Home/brew.txt'; brew list -1 --casks > '/Users/songliyu/Documents/blog/os-mac/.assets/!Home/brew-casks.txt'; brew tap > '/Users/songliyu/Documents/blog/os-mac/.assets/!Home/brew-tap.txt'
```

### 特殊依赖安装

```bash
brew install rustup
rustup-init
```

### Cleanup

```bash
brew cleanup --prune=all -s --dry-run
brew cleanup --prune=all -s
```

## 全局配置

```bash
defaults write -g NSAutomaticWindowAnimationsEnabled -bool false
defaults write -g NSAutomaticPeriodSubstitutionEnabled -bool false
defaults write -g ApplePressAndHoldEnabled -bool false
```

## System settings

<p><img src=".assets/!Home/img/2025-07-09-09-07-43.png" alt="" width=75% style="display: block; margin: auto;"></p>

<p><img src=".assets/!Home/img/2025-07-09-13-49-23.png" alt="" width=75% style="display: block; margin: auto;"></p>

<p><img src=".assets/!Home/img/2025-07-09-13-50-14.png" alt="" width=75% style="display: block; margin: auto;"></p>

<p><img src=".assets/!Home/img/2025-07-09-13-51-02.png" alt="" width=75% style="display: block; margin: auto;"></p>

<p><img src=".assets/!Home/img/2025-07-09-13-52-18.png" alt="" width=75% style="display: block; margin: auto;"></p>

<p><img src=".assets/!Home/img/2025-07-09-13-52-53.png" alt="" width=75% style="display: block; margin: auto;"></p>

<p><img src=".assets/!Home/img/2025-07-09-13-53-44.png" alt="" width=75% style="display: block; margin: auto;"></p>

<p><img src=".assets/!Home/img/2025-07-09-13-54-24.png" alt="" width=75% style="display: block; margin: auto;"></p>

<p><img src=".assets/!Home/img/2025-07-09-13-55-08.png" alt="" width=75% style="display: block; margin: auto;"></p>

## Other settings

### snipaste

<p><img src=".assets/!Home/img/2025-07-09-22-51-58.png" alt="" width=75% style="display: block; margin: auto;"></p>

<p><img src=".assets/!Home/img/2025-07-09-22-53-49.png" alt="" width=75% style="display: block; margin: auto;"></p>

### alt-tab

<p><img src=".assets/!Home/img/2025-07-09-22-55-03.png" alt="" width=75% style="display: block; margin: auto;"></p>

<p><img src=".assets/!Home/img/2025-07-09-22-56-24.png" alt="" width=75% style="display: block; margin: auto;"></p>

### raycast

<p><img src=".assets/!Home/img/2025-07-09-22-57-44.png" alt="" width=75% style="display: block; margin: auto;"></p>

<p><img src=".assets/!Home/img/2025-07-09-22-58-51.png" alt="" width=75% style="display: block; margin: auto;"></p>

<p><img src=".assets/!Home/img/2025-07-09-23-00-03.png" alt="" width=75% style="display: block; margin: auto;"></p>

### [jiggler](https://formulae.brew.sh/cask/jiggler) (deprecated, use mouse-jiggler instead)

> Note: For macOS Tahoe, you should set jiggle mode to `Standard jiggle` (not `Zen jiggle`) to avoid bug.

<p><img src=".assets/!Home/img/2025-07-09-23-01-21.png" alt="" width=75% style="display: block; margin: auto;"></p>

### [mouse-jiggler](https://mousejigglermac.com)

<p><img src=".assets/!Home/img/2025-09-25-14-46-09.png" alt="" width=75% style="display: block; margin: auto;"></p>

### [clash-party](https://formulae.brew.sh/cask/clash-party)

<p><img src=".assets/!Home/img/2025-07-09-23-02-26.png" alt="" width=75% style="display: block; margin: auto;"></p>

### scroll-reverser

<p><img src=".assets/!Home/img/2025-07-09-23-03-22.png" alt="" width=75% style="display: block; margin: auto;"></p>

<p><img src=".assets/!Home/img/2025-07-09-23-04-07.png" alt="" width=75% style="display: block; margin: auto;"></p>

### cursorcerer

<p><img src=".assets/!Home/img/2025-07-09-23-05-39.png" alt="" width=75% style="display: block; margin: auto;"></p>

### [Yoink](https://eternalstorms.at/yoink/mac/)

<p><img src=".assets/!Home/img/2025-07-09-23-06-37.png" alt="" width=75% style="display: block; margin: auto;"></p>

<p><img src=".assets/!Home/img/2025-07-09-23-07-27.png" alt="" width=75% style="display: block; margin: auto;"></p>

### [trex](https://formulae.brew.sh/cask/trex) (deprecated, use bob instead)

<p><img src=".assets/!Home/img/2025-09-10-13-59-19.png" alt="" width=75% style="display: block; margin: auto;"></p>

<p><img src=".assets/!Home/img/2025-09-14-00-08-29.png" alt="" width=75% style="display: block; margin: auto;"></p>

### [bob](https://bobtranslate.com/)

<p><img src=".assets/!Home/img/2025-09-21-14-57-10.png" alt="" width=75% style="display: block; margin: auto;"></p>

<p><img src=".assets/!Home/img/2025-09-21-14-57-29.png" alt="" width=75% style="display: block; margin: auto;"></p>

<p><img src=".assets/!Home/img/2025-09-21-14-58-11.png" alt="" width=75% style="display: block; margin: auto;"></p>

<p><img src=".assets/!Home/img/2025-09-21-15-02-00.png" alt="" width=75% style="display: block; margin: auto;"></p>
