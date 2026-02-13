# Complete Guide to Installing Linuxbrew on NixOS

## Environment Information

- System: NixOS (Linux)
- Proxy: v2raya port 20171
- Installation location: `/home/linuxbrew/.linuxbrew`
- Actual storage: `~/.linuxbrew`

## Installation Steps

### 1. Clone Homebrew Repository

```bash
# Remove old directory (if exists)
rm -rf ~/.linuxbrew

# Clone Homebrew repository using proxy
http_proxy=http://127.0.0.1:20171 https_proxy=http://127.0.0.1:20171 \
GIT_TERMINAL_PROMPT=0 git clone --depth=1 https://github.com/Homebrew/brew.git ~/.linuxbrew/brew
```

### 2. Fix NixOS-Specific Path Issues

On NixOS, bash is located at `/run/current-system/sw/bin/bash` instead of `/bin/bash`. You need to modify the path references in the brew script:

```bash
# Modify /bin/bash references on lines 264 and 312
sed -i '264s|/bin/bash|/run/current-system/sw/bin/bash|' ~/.linuxbrew/brew/bin/brew
sed -i '312s|/bin/bash|/run/current-system/sw/bin/bash|' ~/.linuxbrew/brew/bin/brew

# Modify shebang (first line)
sed -i '1s|#!/bin/bash|#!/run/current-system/sw/bin/bash|' ~/.linuxbrew/brew/bin/brew
```

### 3. Create Standard Directory Structure

Homebrew expects to be installed at `/home/linuxbrew/.linuxbrew` by default. Create symbolic links:

```bash
# Create /home/linuxbrew directory
sudo mkdir -p /home/linuxbrew
sudo chown $USER:users /home/linuxbrew

# Create symbolic link
ln -s /home/$USER/.linuxbrew /home/linuxbrew/.linuxbrew
```

### 4. Configure Environment Variables

Ensure the following configuration is in `~/.bashrc` (usually already exists):

```bash
# Set Homebrew prefix
if [ "$(uname)" = Darwin ]; then
    HOMEBREW_PREFIX=/opt/homebrew
else
    HOMEBREW_PREFIX=/home/linuxbrew/.linuxbrew
fi

# Add to PATH
export HOMEBREW_PREFIX
export PATH="${HOMEBREW_PREFIX}/bin:${PATH}"
```

### 5. Verify Installation

```bash
# Reload configuration
source ~/.bashrc

# Verify
brew --version
brew --prefix
```

## Usage

### Basic Usage

```bash
# Search for packages
brew search <package>

# Install packages
brew install <package>

# List installed packages
brew list

# Uninstall packages
brew uninstall <package>
```

### Install Using Proxy

```bash
http_proxy=http://127.0.0.1:20171 https_proxy=http://127.0.0.1:20171 brew install <package>
```

Or set temporary environment variables:

```bash
export http_proxy=http://127.0.0.1:20171
export https_proxy=http://127.0.0.1:20171
brew install <package>
```

## Limitations of Using Homebrew on NixOS

1. **Precompiled Binaries Incompatible**: Most precompiled binary packages from formulae cannot be used directly on NixOS and need to be compiled from source
2. **Longer Compilation Time**: Since compilation from source is required, installation time is much longer than traditional distributions
3. **Dependency Issues**: Missing system libraries on NixOS may cause compilation failures

## Troubleshooting

### bash: /bin/bash: No such file or directory

You need to modify the shebang and all `/bin/bash` references in the brew script to `/run/current-system/sw/bin/bash`.

### Permission Issues

Ensure the `/home/linuxbrew` directory exists and is owned by the current user:

```bash
sudo chown -R $USER:users /home/linuxbrew
```

### Compilation Failure

If a package fails to compile, you may need to install NixOS-related development dependencies, or consider using the Nix package manager instead.

## Directory Structure

```
~/.linuxbrew/
├── brew/           # Homebrew core files
│   └── bin/
│       └── brew    # Main program
└── bin/
    └── brew        # -> ../brew/bin/brew (symbolic link)

/home/linuxbrew/.linuxbrew -> ~/.linuxbrew (symbolic link)
```
