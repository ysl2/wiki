# tailscale

## Installation

```bash
# Ref: https://login.tailscale.com/admin/welcome
curl -fsSL https://tailscale.com/install.sh | sh

# Might need this: not sure.
# sudo snap remove tailscale

# Set Chinese mirror:
sudo mkdir -p /etc/systemd/system/tailscaled.service.d/
sudo tee /etc/systemd/system/tailscaled.service.d/override.conf > /dev/null <<EOF
[Service]
Environment="HTTP_PROXY=http://127.0.0.1:7890"
Environment="HTTPS_PROXY=http://127.0.0.1:7890"
Environment="ALL_PROXY=socks5://127.0.0.1:7890"
EOF
sudo systemctl daemon-reload
sudo systemctl restart tailscaled
sudo systemctl show tailscaled --property=Environment
# The output should be like: `Environment=HTTP_PROXY=http://127.0.0.1:7890 HTTPS_PROXY=http://127.0.0.1:7890 ALL_PROXY=socks5://127.0.0.1:7890`

# Start tailscale
sudo tailscale up --ssh --accept-dns=false
tailscale status
```
