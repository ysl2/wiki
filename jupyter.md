# jupyter

```bash
#!/bin/bash

# python3 -c "from notebook.auth import passwd; print(passwd())"
# jupyter notebook --ip=0.0.0.0 --port=8888 --notebook-dir=~/Public/jupyter --no-browser
jupyter lab --ip=0.0.0.0 --port=8888 --notebook-dir=~/Public/jupyter --no-browser
# For jupyter's port forwarding:
ssh -L:8888:localhost:8888 silasyu@192.168.3.79
```
