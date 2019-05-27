# Mac Usages

## kill the mysqld process

Homebrew

```bash
#homebrew
launchctl unload -w ~/Library/LaunchAgents/homebrew.mxcl.mysql.plist
launchctl load -w ~/Library/LaunchAgents/homebrew.mxcl.mysql.plist
```