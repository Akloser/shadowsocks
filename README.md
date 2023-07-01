## v2ray

```
bash <(curl -s -L https://git.io/v2ray.sh)
```
```
yum install net-tools

v2ray stop
vi /etc/v2ray/config.json
```
在config.json添加：
`"listen":"66.42.48.247",`
```
firewall-cmd --add-port=6888/tcp --permanent
firewall-cmd --add-port=6888/udp --permanent
firewall-cmd --reload
firewall-cmd --list-all

cd /etc/v2ray/sh
./v2ray.sh
2
1
2
6
```
协议开始使用的tcp，用了两天被封了；
更换成kcp-wireguard，暂时用着；


```
{
        "log": {
                "access": "/var/log/v2ray/access.log",
                "error": "/var/log/v2ray/error.log",
                "loglevel": "warning"
        },
        "inbounds": [
                {
                        "port": 6888,
                        "protocol": "vmess",
                        "listen":"66.42.48.247",
                        "settings": {
                                "clients": [
                                        {
                                                "id": "5a293a6c-0b01-40a6-8025-310bb17beaf0",
                                                "level": 1,
                                                "alterId": 0
                                        }
                                ]
                        },
                        "streamSettings": {
                                "network": "kcp",
                                "kcpSettings": {
                                        "header": {
                                                "type": "wireguard"
                                        }
                                }
                        },
                        "sniffing": {
                                "enabled": true,
                                "destOverride": [
                                        "http",
                                        "tls"
                                ]
                        }
                }
                //include_ss
                //include_socks
                //include_mtproto
                //include_in_config
                //
        ],
        "outbounds": [
                {
                        "protocol": "freedom",
                        "settings": {
                                "domainStrategy": "UseIP"
                        },
                        "tag": "direct"
                },
                {
                        "protocol": "blackhole",
                        "settings": {},
                        "tag": "blocked"
        }
                //include_out_config
                //
        ],
        "dns": {
                "servers": [
                        "https+local://dns.google/dns-query",
                        "8.8.8.8",
                        "1.1.1.1",
                        "localhost"
                ]
        },
        "routing": {
                "domainStrategy": "IPOnDemand",
                "rules": [
            {
                "type": "field",
                "ip": [
                    "geoip:private"
                ],
                "outboundTag": "blocked"
            }
                        ,
                        {
                                "type": "field",
                                "domain": [
                                        "domain:epochtimes.com",
                                        "domain:epochtimes.com.tw",
                                        "domain:epochtimes.fr",
                                        "domain:epochtimes.de",
                                        "domain:epochtimes.jp",
                                        "domain:epochtimes.ru",
                                        "domain:epochtimes.co.il",
                                        "domain:epochtimes.co.kr",
                                        "domain:epochtimes-romania.com",
                                        "domain:erabaru.net",
                                        "domain:lagranepoca.com",
                                        "domain:theepochtimes.com",
                                        "domain:ntdtv.com",
                                        "domain:ntd.tv",
                                        "domain:ntdtv-dc.com",
                                        "domain:ntdtv.com.tw",
                                        "domain:minghui.org",
                                        "domain:renminbao.com",
                                        "domain:dafahao.com",
                                        "domain:dongtaiwang.com",
                                        "domain:falundafa.org",
                                        "domain:wujieliulan.com",
                                        "domain:ninecommentaries.com",
                                        "domain:shenyun.com"
                                ],
                                "outboundTag": "blocked"
                        }                       ,
                {
                    "type": "field",
                    "protocol": [
                        "bittorrent"
                    ],
                    "outboundTag": "blocked"
                }
                        //include_ban_ad
                        //include_rules
                        //
                ]
        },
        "transport": {
                "kcpSettings": {
            "uplinkCapacity": 100,
            "downlinkCapacity": 100,
            "congestion": true
        }
        }
}

```

## vps服务器地址
- new york $3.5,便宜
- tokyo $5,用了两天被封
- seoul， $5,ping不通
- Singapore，$5,延迟只有91ms，暂时在用

## shadowsocks-server
```
wget --no-check-certificate  https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks.sh
chmod +x shadowsocks.sh
./shadowsocks.sh 2>&1 | tee shadowsocks.log
```

```
wget -N --no-check-certificate https://raw.githubusercontent.com/luvvien/ssr-install-shellscript/master/ssr.sh && chmod +x ssr.sh && bash ssr.sh
```
## 安装netstat工具
```
yum install net-tools
```


windows、Mac系统 ss下载地址：https://www.sednax.com/ (https://www.sednax.com/)
windows系统 ssr下载地址：https://github.com/shadowsocksrr/shadowsocksr-csharp/releases/download/4.9.0/ShadowsocksR-win-4.9.0.zip
(https://github.com/shadowsocksrr/shadowsocksr-csharp/releases/download/4.9.0/ShadowsocksR-win-4.9.0.zip)
Android系统 ssr下载地址：https://github.com/shadowsocksrr/shadowsocksr-android/releases/download/3.5.4/shadowsocksr-android-3.5.4.apk
(https://github.com/shadowsocksrr/shadowsocksr-android/releases/download/3.5.4/shadowsocksr-android-3.5.4.apk)
Mac系统 ssr下载地址：https://github.com/qinyuhang/ShadowsocksX-NG-R/releases/download/1.4.3-R8-build3/ShadowsocksX-NG-R8.dmg
(https://github.com/qinyuhang/ShadowsocksX-NG-R/releases/download/1.4.3-R8-build3/ShadowsocksX-NG-R8.dmg)
ios系统：很抱歉，大陆下载不了。请淘宝买一个非大陆的Apple id，然后登陆搜索 wingy 、 outline 、 SuperWingy 、 RocketWingy 等软件，你也
可以直接搜ss或者ssr，会出现相关软件的。

## shadowsocks-windows
[shadowsocks-windows](https://github.com/shadowsocks/shadowsocks-windows)

## shadowsocks-android
[shadowsocks-android](https://github.com/shadowsocks/shadowsocks-android)

## Others
- shadowsocksR-server(不能使用2021-01-16)
```
wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocksR.sh
chmod +x shadowsocksR.sh
./shadowsocksR.sh 2>&1 | tee shadowsocksR.log
```

- 协议与混淆
<https://www.bilibili.com/read/cv4040403/>
