# xray-websocket-tls-nginx

## 警告⚠：此技术仅限用于个人搭建游戏加速器使用！！！若用于其他违法目的，后果自负！！！

手动搭建xray服务器(vmess+websocket+tls)，并部署网页页面，支持cdn中转

KVM/XEN机器执行(CentOS7):

`yum install -y gcc wget && wget https://raw.githubusercontent.com/HXHGTS/xray-websocket-tls-nginx/main/v2ray.c -O v2ray.c && chmod +x v2ray.c && gcc -o v2ray v2ray.c && ./v2ray`

OpenVZ机器执行(CentOS7):

`yum install -y gcc wget && wget https://raw.githubusercontent.com/HXHGTS/xray-websocket-tls-nginx/main/v2ray_no_bbr.c -O v2ray.c && chmod +x v2ray.c && gcc -o v2ray v2ray.c && ./v2ray`

KVM/XEN机器执行(Debian8):

`apt-get install -y gcc wget && wget https://raw.githubusercontent.com/HXHGTS/xray-websocket-tls-nginx/main/v2ray-debian.c -O v2ray.c && chmod +x v2ray.c && gcc -o v2ray v2ray.c && ./v2ray`

KVM/XEN/OVZ机器执行(Debian10):

`apt-get install -y gcc wget && wget https://raw.githubusercontent.com/HXHGTS/xray-websocket-tls-nginx/main/v2ray-ovz-debian10.c -O v2ray.c && chmod +x v2ray.c && gcc -o v2ray v2ray.c && ./v2ray`

第一次点击安装后会自动升级系统内核并触发重启，重启后输入

`./v2ray`

CDN套用方法请参看[CDN套用方法](/cdn.md)

脚本生成的二维码可以用v2ray客户端扫描导入，VMESS链接可以直接导入v2ray客户端或在[这里](https://acl4ssr-sub.github.io/)生成Clash链接以导入Clash

### 安装前准备：

1.一个域名，与服务器ip做好dns解析

2.该域名必须提前申请SSL证书用于加密（后续考虑加入自动申请证书），将证书(*.cer/*.crt/*.pem)文件命名为1.pem，将私钥(*.key/*.pem)文件命名为2.pem，放在/root目录下(SSL证书申请:[腾讯云](https://console.cloud.tencent.com/ssl) [阿里云](https://common-buy.aliyun.com/?spm=5176.b5912525.0.0.3c07GExwGExwfv&commodityCode=cas) [FreeSSL](https://freessl.cn/))

3.脚本仅支持CentOS7系统

4.脚本执行需要root权限登录系统，AWS等特殊机型打开root权限方法[看这里](https://hxhgts.github.io/AWSECSRoot/)

5.请在服务器后台防火墙放行tcp2053(https)端口
