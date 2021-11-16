### 套用CDN

#### 方案1(域名已托管在Cloudflare)(免费无限量)

1.找到dns记录中服务器的域名的A记录与AAAA记录(如果有ipv6的话)

2.点亮云朵☁️

#### 方案2(域名未托管在Cloudflare)(免费额度每天10w次请求)

1.申请Cloudflare账号

2.打开Workers，管理Workers，创建Worker

3.输入代码
```
addEventListener(
"fetch",event => {
let url=new URL(event.request.url);
url.hostname="*************";
let request=new Request(url,event.request);
event. respondWith(
fetch(request)
)
}
)
```

*************用服务器域名替换

4.修改一个好记的名称，比如***.***.workers.dev,填入v2ray的ws-headers中，并将ip改为cloudflare的可用ip

一个典型Clash配置:
```
  - {name: xxxxxxxxxx, server: 1.0.0.1, port: 443, type: vmess, uuid: xxxxxxxxx-xxxx-xxxx-xxxxxx, alterId: 0, cipher: auto, tls: true, network: ws, ws-path: /xxxxx, ws-headers: {Host: xxx.xxxxxx.workers.dev}}
```
另一种写法:
```
  - name: xxxxxxxxxx
    server: 1.0.0.1
    port: 443
    type: vmess
    uuid: xxxxxxxxx-xxxx-xxxx-xxxxxx
    alterId: 0
    cipher: auto
    tls: true
    network: ws
    ws-path: /iso
    ws-headers:
      Host: xxxxxxxxxx
    udp: true
```
1.0.0.1请下载[Cloudflare ip优选工具](https://github.com/XIU2/CloudflareSpeedTest)，根据实际带宽优选CDN加速ip，最后用优选的ip进行替换，host填Worker的网址，不是服务器网址！！！
