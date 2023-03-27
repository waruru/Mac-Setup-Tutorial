## peco
### インストール
```zsh
brew install peco
```

### alias
```zsh
echo "alias sshp=\"grep -w Host ~/.ssh/config | peco | awk '{print \$2}' | xargs -o -n 1 ssh\"" >> ~/.zshrc
```
