# miniserve

## Installation

```bash
brew install miniserve
```

## Usage

```bash
miniserve ~ -qu -a "$YOUR_USERNAME":"$YOUR_PASSWORD" -p 36009 &; disown
autossh -M 37009 -NfR 47.xxx.xxx.227:38009:localhost:36009 -p 36000 yusongli@47.xxx.xxx.227

miniserve /mnt/nas -qu -a "$YOUR_USERNAME":"$YOUR_PASSWORD" -p 36010 &; disown
autossh -M 37010 -NfR 47.xxx.xxx.227:38010:localhost:36010 -p 36000 yusongli@47.xxx.xxx.227
```
