# SSR

## ubuntu安装ssr

```
sudo apt update
wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocksR.sh
chmod +x shadowsocksR.sh
./shadowsocksR.sh 2>&1 | tee shadowsocksR.log

```

## 常用命令
```
/etc/init.d/shadowsocks start  //启动
/etc/init.d/shadowsocks stop //停止
/etc/init.d/shadowsocks restart //重启
/etc/init.d/shadowsocks status //查看状态
```

## Configuration file

```bash
/etc/shadowsocks.json # configuration file
```

## 卸载ssr
```
./shadowsocksR.sh uninstall
```

## 多用户配置
```
{
"server":"0.0.0.0",
"server_ipv6": "[::]",
"local_address":"127.0.0.1",
"local_port":1080,
"port_password":{
    "8989":"password1",
    "8990":"password2",
    "8991":"password3"
},
"timeout":300,
"method":"aes-256-cfb",
"protocol": "origin",
"protocol_param": "",
"obfs": "plain",
"obfs_param": "",
"redirect": "",
"dns_ipv6": false,
"fast_open": false,
"workers": 1
}
```
