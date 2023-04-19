vpn服务器ip被封解决方案

一．	在服务器和客户端分别安装内网穿透
安装地址：Customers · Tailscale
二．	搭建 ShadowsocksR (SSR) 服务端（centos为例）
yum install python-setuptools && easy_install pip 
然后你可以通过 pip 安装 ShadowsocksR:
pip install shadowsocks
安装完成之后，你就可以创建一个 ShadowsocksR 配置文件，并使用该配置文件来运行 ShadowsocksR 服务端。配置文件可以是 JSON 格式的，如下所示:


mkdir -p /path/to/config.json
vi  /path/to/config.json

写入
{
    "server":"10.50.50.66",#换成你的内网穿透ip
    "server_port":8388,
    "local_address":"127.0.0.1",
    "local_port":1080,
    "password":"123456",#密码
    "timeout":600,
    "method":"aes-256-cfb"
}
最后，你可以使用以下命令来启动 ShadowsocksR 服务端：
ssserver -c /path/to/config.json -d start


