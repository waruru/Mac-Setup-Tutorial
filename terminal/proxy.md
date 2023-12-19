`~/.switch_proxy`
```:sh
proxy=YOUR_PROXY_HOST:YOUR_PROXY_PORT
switch_trigger_location=YOUR_LOCATION
switch_trigger_network=YOUR_ACCESS_POINT

function set_proxy() {
  export http_proxy=$proxy
  export ftp_proxy=$proxy
  export all_proxy=$proxy
  export https_proxy=$proxy

  git config --global http.proxy $proxy
  git config --global https.proxy $proxy
  git config --global url."https://".insteadOf git://
}

function unset_proxy() {
  unset http_proxy
  unset ftp_proxy
  unset all_proxy
  unset https_proxy

  git config --global --unset http.proxy
  git config --global --unset https.proxy
  git config --global --unset url."https://".insteadOf
}

if [ "`networksetup -getcurrentlocation`" = "$switch_trigger_location" -a "`networksetup -getairportnetwork en0 | awk '{print $4}'`" = "$switch_trigger_network" ]; then
  echo "Switch to proxy for office network"
  set_proxy
else
  echo "Unset proxy settings"
  unset_proxy
fi
```

`~/.zprofile`
```:sh
# Proxy
alias nswitch="source ~/.switch_proxy"
```

ターミナル起動時に実行するように以下も追記
```:sh
nswitch
```

[参考サイト](https://qiita.com/shiraco/items/8971e38cbbd42ea32d73)
