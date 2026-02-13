# OpenClaw Installation Guide (NixOS)

This document records the complete process of successfully installing OpenClaw on NixOS.

## System Environment

- **Operating System**: NixOS 26.05 (Yarara)
- **Architecture**: x86_64
- **Node.js**: v24.12.0 (OpenClaw requires >= 22)
- **npm**: 11.6.2
- **Proxy**: v2raya (port 20171)

## Installation Steps

### 1. Configure npm User Directory

On NixOS, `/nix/store` is read-only, so npm packages need to be installed to a user directory:

```bash
mkdir -p ~/.npm-global
echo 'export NPM_CONFIG_PREFIX=~/.npm-global' >> ~/.bashrc
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.bashrc
export PATH=~/.npm-global/bin:$PATH
```

### 2. Install cmake

OpenClaw depends on `node-llama-cpp`, which requires cmake for compilation. Since nix downloads are slow, download the cmake binary directly:

```bash
# Use proxy to accelerate download
export http_proxy=http://127.0.0.1:20171
export https_proxy=http://127.0.0.1:20171

# Download and extract cmake
cd ~
wget https://github.com/Kitware/CMake/releases/download/v4.1.2/cmake-4.1.2-linux-x86_64.tar.gz
tar -xzf cmake-4.1.2-linux-x86_64.tar.gz
rm cmake-4.1.2-linux-x86_64.tar.gz

# Add to PATH
echo 'export PATH=~/cmake-4.1.2-linux-x86_64/bin:$PATH' >> ~/.bashrc
export PATH=~/cmake-4.1.2-linux-x86_64/bin:$PATH

# Verify installation
cmake --version
```

### 3. Install OpenClaw

```bash
# Ensure cmake is in PATH
export PATH=~/cmake-4.1.2-linux-x86_64/bin:$PATH

# Use proxy to accelerate npm download
export http_proxy=http://127.0.0.1:20171
export https_proxy=http://127.0.0.1:20171

# Install OpenClaw globally
npm install -g openclaw@latest
```

The installation process takes approximately 10 minutes and will download and compile 675 packages.

### 4. Verify Installation

```bash
source ~/.bashrc
openclaw --version
```

Output: `2026.2.9`

## Usage

### Initialize Configuration

```bash
openclaw onboard --install-daemon
```

The wizard will guide you through:
- Gateway setup
- Workspace configuration
- Channel configuration (WhatsApp, Telegram, Slack, Discord, etc.)
- AI model configuration (Anthropic Claude or OpenAI)

### Start Gateway

```bash
openclaw gateway --port 18789 --verbose
```

## Gateway Proxy Configuration

The Telegram API requires a proxy in China. A startup script has been created:

```bash
#!/bin/bash
export http_proxy=http://127.0.0.1:20171
export https_proxy=http://127.0.0.1:20171
exec ~/.npm-global/bin/openclaw gateway "$@"
```

### Send Messages

```bash
# Send to specified channel
openclaw message send --to +1234567890 --message "Hello from OpenClaw"

# Chat with assistant
openclaw agent --message "Help me with..." --thinking high
```

## Supported Platforms

- WhatsApp
- Telegram
- Slack
- Discord
- Google Chat
- Signal
- iMessage
- Microsoft Teams
- WebChat
- BlueBubbles
- Matrix
- Zalo / Zalo Personal

## FAQ

### Q: nix-shell or nix profile cmake installation is slow?

A: NixOS default mirrors may be slow. It is recommended to:
1. Configure a proxy (like v2raya in this document)
2. Download cmake binary directly

### Q: npm install -g fails with permission errors?

A: NixOS's `/nix/store` is read-only. You must configure npm to use a user directory (see step 1).

### Q: node-llama-cpp compilation fails?

A: Ensure cmake is installed and correctly added to PATH.

### Q: openclaw gateway status shows unhealthy service status?

A: This is usually a systemd service configuration issue. Follow these steps to troubleshoot:

1. **Check service status**:
```bash
systemctl --user status openclaw-gateway
```

2. **Check if service file link is valid**:
```bash
ls -la ~/.config/systemd/user/openclaw-gateway.service
```

3. **View the actual path pointed to by the symbolic link**:
```bash
readlink -f ~/.config/systemd/user/openclaw-gateway.service
```

If `readlink` output is empty or indicates the file doesn't exist, the link target has been deleted.

4. **Delete invalid link and reinstall service**:
```bash
# Delete invalid service file
rm ~/.config/systemd/user/openclaw-gateway.service

# Reload systemd
systemctl --user daemon-reload

# Reinstall service
openclaw gateway install

# Start service
systemctl --user start openclaw-gateway
```

5. **Verify service status**:
```bash
openclaw gateway status
```

Should display `Runtime: running` and `RPC probe: ok`.

### Q: Telegram channel cannot connect (fetch failed)?

A: The Telegram API requires a proxy in China, but systemd services don't inherit user proxy environment variables by default.

**Solution**: Edit the service file to add proxy configuration:

```bash
# Edit service file
nano ~/.config/systemd/user/openclaw-gateway.service
```

Add at the end of the `Environment` line in the `[Service]` section:

```ini
Environment=http_proxy=http://127.0.0.1:your-proxy-port
Environment=https_proxy=http://127.0.0.1:your-proxy-port
```

Restart the service after saving:

```bash
systemctl --user daemon-reload
systemctl --user restart openclaw-gateway
```

Verify the fix:

```bash
openclaw doctor
```

Should display `Telegram: ok (@your-username)`.

## References

- [OpenClaw Official Website](https://openclaw.ai)
- [OpenClaw Documentation](https://docs.openclaw.ai)
- [GitHub Repository](https://github.com/openclaw/openclaw)
- [Getting Started Guide](https://docs.openclaw.ai/start/getting-started)

---

Installation Date: 2026-02-11
OpenClaw Version: 2026.2.9
