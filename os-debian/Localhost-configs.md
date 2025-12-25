# [os-debian] Localhost configs

## For ubuntu desktop's specific

`~/.bashrc.localhost.pre`

```bash
#!/bin/bash

# NOTE: Ubuntu desktop uses ibus, so these variables should be set to ibus.
# Otherwise the input method cannot be changed in firefox.
export GTK_IM_MODULE=ibus
export QT_IM_MODULE=ibus
export XMODIFIERS=@im=ibus
export SDL_IM_MODULE=ibus
```
