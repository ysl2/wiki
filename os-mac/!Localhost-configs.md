# [os-mac] Localhost configs

`~/.bashrc.localhost.pre`

```bash
MYCONDA=/opt/homebrew/Caskroom/miniforge/base
```

---

`~/.bashrc.localhost.post`

```bash
myquit() {
  [ -n "$TMUX" ] && exit || aerospace close
}
alias :q='myquit'
```
