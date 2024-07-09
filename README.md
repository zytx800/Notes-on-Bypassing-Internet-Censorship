# Notes on Bypassing Internet Censorship in Myanmar

## Choosing cloud virtual machine (VPS) providers

### 1. Amazon AWS Lightsail (Recommended)

- 3 months free tier available for new customers
- Free 3 TB data traffic monthly to internet, see [details](https://aws.amazon.com/lightsail/faq/)
- 2 vCPUs, 2 GB RAM, 60GB SSD
- Suport account registration from Myanmar
- Support VISA, Mastercard and JCB debit or credit cards issued by Myanmar's Banks (Note: it doesn't support Prepaid Cards)
- [Website link](https://aws.amazon.com/free/compute/lightsail/)

### 2. Amazon AWS EC2

- 12 months free tier available for new customers
- 1 x t2.micro instance per month in free tier
- Free 100 GB data traffic monthly to internet, see [details](https://aws.amazon.com/ec2/pricing/on-demand/)
- 1 vCPUs, 1 GB RAM and 30GB SSD
- Suport account registration from Myanmar
- Support VISA, Mastercard and JCB debit or credit cards issued by Myanmar's Banks (Note: it doesn't support Prepaid Cards)
- [Website link](https://aws.amazon.com/ec2/)

### 3. Microsoft Azure

- $200 credit for 12 months for new customers
- Free 100 GB data traffic monthly to internet, see [details](https://azure.microsoft.com/en-us/pricing/details/bandwidth/)
- Azure account registration is not supported for Myanmar region, but VISA credit cards issued by Myanmar's Banks can be used. (Ask your friends who are in a Microsoft Azure supported region to help you sign up)
- [Website link](https://azure.microsoft.com/en-us/free)

### 4. Google Cloud Platform

- $300 credit for 12 months for new customers
- 1 x ec2-miro instance per month in free tier
- Free 200 GB data traffic monthly to internet, see [details](https://cloud.google.com/vpc/network-pricing)
- GCP account registration is not supported for Myanmar region, but VISA, Mastercard and JCB debit or credit cards issued by Myanmar's Banks can be used. (Ask your friends who are in a GCP supported region to help you sign up)
- [Website link](https://cloud.google.com/free/)

### 5. DigitalOcean (Not Tested)

- $200 free credit for 60 days for new customers
- [Website link](https://try.digitalocean.com/freetrialoffer/)

### 6. Oracle Cloud Infrastructure  (Not Tested)

- $300 free credit for 30 days for new customers
- [Website link](https://www.oracle.com/sg/cloud/free/)


### 7. Others (Not Tested)

- [AlexHost](https://alexhost.com/vps/#unmanaged-link)
- [aeza.net](https://aeza.net/virtual-servers)
- [IONOS](https://www.ionos.it/server/vps)


## Choosing circumvention methods

### Proxy / VPN Platforms

#### V2Ray

- As the core part of project V, V2Ray is a tool that provides a secure platform for making private networks.
- V2Ray was developed in 2015 as an alternative to Shadowsocks.
- V2Ray is a powerful proxy platform that supports a variety of protocols, among them, only the VMESS protocol is an exclusive encrypted commnunication protocol originally created by the V2Ray community.
- V2Ray currently supports Blackhole, Dodkodemo-door, Freedom, HTTP, MTProto, Shadowsocks, Socks and VMess protocols.
- As of December 2019, V2Ray's optional transport layer configurations are: TCP, mKCP, WebSocket, HTTP/2, DomainSocket, QUIC. Among them, mKCP, QUIC and TCP are used to optimize network quality, WebSocket is used for camouflage, HTTP/2 and DomainSocket are used for transmission and TLS encryption.
- Learn more [Project V Official Website](https://www.v2ray.com/en/), [GitHub v2fly/v2ray-core](https://github.com/v2fly/v2ray-core)

#### Xray

- Xray is completely similar to V2Ray, and Xray is the core module of Project X.
- Since rprx, the author of Xray and XTLS, was once an important member of the V2fiy community, Xray directly forked all V2Ray functions, optimized performance, added new functions, and created the original VLESS and XTLS protocols, making Xray a superset of V2Ray in terms of functionality and fully compatible with V2Ray.
- In short, Xray is a branch of V2Ray. Xray is a superset of V2Ray.
- Xray XTLS protocol aims to enhance communication efficiency and allows Xray to work at a faster speed.
- XTLS, one of Xray’s key features, is an improvement over V2Ray’s WS TLS protocol, which is less optimized for communication over the Internet. In addition to XTLS.
- Xray also features a powerful routing system that is highly customizable.
- Learn more [Project X Official Website](https://xtls.github.io/en/), [GitHub - XTLS/Xray-core](https://github.com/XTLS/Xray-core?tab=readme-ov-file)

### Protocol notes

#### VMESS

- VMESS is a encrypted transmission protocol dedicated to V2Ray.
- It is divided into inbound and outbound parts, and usually used as a bridge between th V2Ray client and the server.
- Because of the added obfuscation and encryption, it is said to be safer than Shadowsocks and more difficult for censors to detect VPN  activity as it seems like regular Internet traffic.

#### VLESS

- VLESS is the newest protocol of V2Ray and the main difference between VLESS and VMESS is that VLESS uses a simplified handshake process to reduce resource usage and increase
performance. So it is lightweight and efficient.
- It can operate faster and use less CPU power than other protocols.
- VLESS also uses the latest version of TLS to provide better encryption and authentication.

### Trojan

- Trojan started development in 2017.
- Trojan, originally referred to Trojan horse, is a computer virus program. However, the Trojan we are talking about today is a new scientific Internet technology, the full name is Trojan-GFW, which is one of the most successful scientific Internet camouflage technologies.
- You can think of Trojan as a simplified version of V2Ray's "WS+TLS" mode, which is faster than V2Ray, more realistic than V2Ray in camouflage, and more difficult to be identified by GFW.
- Trojan processes HTTPS requests from the outside world. If it is legitimate, it will provide services for the request. Otherwise, it will transfer the traffic to web servers such as Caddy and Nginx, which will provide web access services for it.
-  Based on the entire interactive process, this can make your VPS more like a normal web server, because all Trojan behaviors are consistent with
web servers such as Caddy and Nginx, and no additional features are introduced, making it difficult to identify.

### Trojan-Go

- Compared with the original Trojan, Trojan-Go has some more features, such as multiplexing (smux) to reduce latency, improve concurrent performance, CDN traffic transfer, etc.
- Under normal circumstances, the clients of Trojan and Trojan-Go are universal, and the client of Trojan can be used for the connection of Trojan-Go.
- However, the original Trojan does not support some multiplexing and other functions. If you need to use these functions, you need to use it with a special Trojan-Go client.

### Shadowsocks (Not recommended)

- Shadowsocks is one of the first protocols developped in China specifically to bypass the GFW.
- Development started on April 20, 2012. It's original developper was forced to stop his/her work on the project due to outside pressure. Work on the protocol continues on till this day via various forks on the original project.
- Currently, Burmese operators already have the technology to detect Shadowscocks traffics using GFW.
