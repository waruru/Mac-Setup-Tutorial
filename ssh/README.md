## peco
### インストール
```zsh
brew install peco
```

### alias
```zsh
echo "alias sshp=\"grep -w Host ~/.ssh/config | peco | awk '{print \$2}' | xargs -o -n 1 ssh\"" >> ~/.zshrc
```

## nping
`ping`コマンドでポート指定
### インストール
```zsh
brew install nmap
```

### 使用方法
```zsh
nping 127.0.0.1 -p 3306
```
