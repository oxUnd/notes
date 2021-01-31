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
