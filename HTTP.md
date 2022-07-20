# HTTP

hypertext transfer protocol

_TCP/IP 网络模型分层_

## 1. 应用层

规定传输数据的格式,比如 http 报文

常见协议有: HTTP,FTP,Telnet,DNS,SMTP

_terms_

1. URL(uniform resource locator): http:域名/ip+端口+路径+参数+锚点(不会在 request 报文中)
2. DNS(domain name system): 返回 url->ip 的映射,IP 协议参见网络层
   > 使用 `nslookup 域名` 命令会返回查询域名的 IP 地址
   > URL 和 IP 有一对多和多对一的关系,分别用于均衡负载和多域名同一个 ip
3. 域名层级关系

   > ![域名层级关系](https://cdn.xiaolincoding.com/gh/xiaolincoder/ImageHost/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C/%E9%94%AE%E5%85%A5%E7%BD%91%E5%9D%80%E8%BF%87%E7%A8%8B/5.jpg)

4. HTTP 报文

   a. 请求 request line-header-body

   ```
   GET /index?wd=hi HTTP/1.1
   Host: localhost:8888
   Accept: text/html
   Content-Type: 请求体的格式
   ```

   使用 curl 发送请求

   ```
   curl -v http://localhost:8080/
   curl -X POST --header 'Name:Value' --data 'content' url
   ```

   b. 响应 response

   ```
   HTTP/1.1 200 OK
   Content-Type: 响应体的格式(i.e.,text/html;charset=utf-8)
   ```

   使用 node 获取请求,发送响应

   ```
   request.method/request.headers['method'];
   /* path |  */

   response.statusCode = 200
   response.setHeader("Content-Type", "text/html;charset=utf-8");
   /*  |*/
   response.write(` `);
   response.end();

   ```

   _状态码_

   > 2 correct
   > 3 redirect
   > 4 bad request
   > 5 server error

## 2. 传输层

协议:TCP UDP

数据形式: TCP 报文(TCP 头部+HTTP 报文)...

_terms_

1. port
   > HTTP 默认端口为 80,HTTPS 默认端口号为 443
   > 同一台计算机有很多发送数据的程序,端口用来标识.
2. 握手
3. 流量控制
4. 拥塞控制

## 3. 网络层

协议: IP

数据形式: 网络包

_terms_

1. IP 地址: 外网/内网 外网对应现实中的地址
   > ping 域名/ip 地址
2. 路由表
3. MAC 地址
   > ARP 协议

## 4. 数据链路层
