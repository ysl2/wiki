# openclaw

## Add browser support

```bash
openclaw browser extension install
openclaw browser extension path

# The command above will show this path: `~/.openclaw/browser/chrome-extension`
```

Enable chrome's developer mode, and add the path above into chrome extensions page.

## Add web_search support

```bash
openclaw configure --section web
# Then, enter the brave search api key.
```

## Add full access

`nvim ~/.openclaw/openclaw.json`

```json
{
  ...
  "tools": {
    "profile": "full"
  },
  ...
}
```
