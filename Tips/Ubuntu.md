# 0x000

# 0x001 代理
## socks5 to http

使用软件 **privoxy**

```bash
apt install privoxy
```
配置

```bash
systemctl status privoxy
```

配置文件

```bash
vi /etc/privoxy/config
```

```etc
# 把本地 HTTP 流量转发到本地 1080 SOCKS5 代理
forward-socks5t / 127.0.0.1:10800 .
# 可选，默认监听本地连接
listen-address 127.0.0.1:8811
```

## APT 代理

支持 http 代理

```bash
sudo apt-get -o Acquire::http::proxy="http://127.0.0.1:8811/" install <xxx>
```

# 0x002 软件

## 尝试使用 fcitx5

使用 ppa

```bash
sudo add-apt-repository ppa:hosxy/fcitx5
```

```bash
sudo apt install fcitx5 fcitx5-pinyin
```

Ubuntu 20.04 KDE 环境下 fcitx5-configtool 缺少组件无法使用，请在 fcitx5 未启动状态下手动配置，不然会被覆盖。

```bash
vi ~/.config/fcitx5/profile

[Groups/0]
# Group Name
Name=Default
# Layout
Default Layout=us
# Default Input Method
DefaultIM=pinyin

[Groups/0/Items/0]
# Name
Name=keyboard-us
# Layout
Layout=

[Groups/0/Items/1]
# Name
Name=pinyin
# Layout
Layout=

[GroupOrder]
0=Default

```

<kbd>CTRL</kbd>-<kbd>SPECE</kbd> 切换输入法。

# 0x003 开发

## 动态链接库找不到

在 64 位机器上，有时候需要 32 位的 `.so` 动态链接库，这时候需要安装它们，我们可以尝试安装 `lib32*`

比如你缺的是 `libz.so.1`

执行以下命令安装它即可。

```
# apt install lib32z1 lib32z1-dev
```



