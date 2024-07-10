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
- V2Ray is a powerful proxy platform that supports a variety of protocols, among them, only the VMess protocol is an exclusive encrypted commnunication protocol originally created by the V2Ray community.
- V2Ray currently supports Blackhole, Dodkodemo-door, Freedom, HTTP, MTProto, Shadowsocks, Socks and VMess protocols.
- As of December 2019, V2Ray's optional transport layer configurations are: TCP, mKCP, WebSocket, HTTP/2, DomainSocket, QUIC. Among them, mKCP, QUIC and TCP are used to optimize network quality, WebSocket is used for camouflage, HTTP/2 and DomainSocket are used for transmission and TLS encryption.
- Links: 
- [Project V Official Website](https://www.v2ray.com/en/)
- [GitHub v2fly/v2ray-core](https://github.com/v2fly/v2ray-core)
- See Xray links for more setup servers and client apps

#### Xray

- Xray is completely similar to V2Ray, and Xray is the core module of Project X.
- Since rprx, the author of Xray and XTLS, was once an important member of the V2fly community, Xray directly forked all V2Ray functions, optimized performance, added new functions, and created the original VLESS and XTLS protocols, making Xray a superset of V2Ray in terms of functionality and fully compatible with V2Ray.
- In short, Xray is a branch of V2Ray and Xray is a superset of V2Ray.
- Xray XTLS protocol aims to enhance communication efficiency and allows Xray to work at a faster speed.
- XTLS, one of Xray’s key features, is an improvement over V2Ray’s WS TLS protocol, which is less optimized for communication over the internet.
- Xray also features a powerful routing system that is highly customizable.
- Links:
- [Project X Official Website](https://xtls.github.io/en/)
- [GitHub - XTLS/Xray-core](https://github.com/XTLS/Xray-core)
- [Install Xray Core on Debian/Ubuntu](https://github.com/zytx800/Notes-on-Bypassing-Internet-Censorship/tree/main/xray)
- Android apps
- [v2rayNG - Android - Download from Play Store](https://play.google.com/store/apps/details?id=com.v2ray.ang)
- [Hiddify - Android - Download from Play Store](https://play.google.com/store/apps/details?id=app.hiddify.com)
- [V2Box  - Android - Download from Play Store](https://play.google.com/store/apps/details?id=dev.hexasoftware.v2box&hl=en_SG)
- iOS apps
- [FoXray  - iOS - Download from App Store](https://apps.apple.com/us/app/foxray/id6448898396)
- [V2Box - iOS - Download from App Store](https://apps.apple.com/us/app/v2box-v2ray-client/id6446814690)
- [Streisand - iOS - Download from App Store](https://apps.apple.com/us/app/streisand/id6450534064)
- Windows apps
- [Hiddify](https://apps.microsoft.com/detail/9pdfnl3qv2s5?hl=en-us&gl=SG)
- [v2rayN](https://github.com/2dust/v2rayN/releases)
- [Qv2ray](https://github.com/Qv2ray/Qv2ray/releases)
- macOS (arm64 & x64)
- [FoXray](https://apps.apple.com/us/app/foxray/id6448898396)
- [V2RayXS](https://github.com/tzmax/V2RayXS/releases)
- [Furious](https://github.com/LorenEteval/Furious)
- [Qv2ray](https://github.com/Qv2ray/Qv2ray/releases)

#### SoftEther

- SoftEther VPN is free open-source, cross-platform, multi-protocol VPN client and VPN server software, developed as part of Daiyuu Nobori's master's thesis research at the University of Tsukuba.
- VPN protocols such as SSL-VPN (HTTPS), L2TP/IPsec, OpenVPN, and Microsoft Secure Socket Tunneling Protocol are provided in a single VPN server. Among those protocols, SoftEther's SSL-VPN (HTTPS) is currently resistant to GFW's filters.
- Links:
- [SoftEther Official Website](https://www.softether.org/)
- [GitHub - SoftEtherVPN/SoftEtherVPN](https://github.com/SoftEtherVPN/SoftEtherVPN)
- [Setup SoftEther VPN Server on Debian/Ubuntu](https://github.com/zytx800/Notes-on-Bypassing-Internet-Censorship/tree/main/softether)
- [Download SoftEtherVPN client for Windows from GitHub releases](https://github.com/SoftEtherVPN/SoftEtherVPN/releases)

### Protocol notes

#### VMess

- VMess is a encrypted transmission protocol dedicated to V2Ray.
- VMess is a stateless protocol, which means that data can be transmitted directly between the client and the server without the need for a handshake. Each data transmission has no impact on other data transmissions before or after it.
- When a VMess client initiates a request, the server checks whether the request comes from a legitimate client. If the validation passes, the server forwards the request and sends the obtained response back to the client.
- VMess uses an asymmetric format, meaning that the requests sent by the client and the responses from the server use different formats.
- VMess is a TCP-based protocol, and all data is transmitted using TCP.
- It is divided into inbound and outbound parts, and usually used as a bridge between th V2Ray client and the server.
- Because of the added obfuscation and encryption, it is said to be safer than Shadowsocks and more difficult for censors to detect VPN  activity as it seems like regular Internet traffic.
- [Learn more](https://xtls.github.io/en/development/protocols/vmess.html)

#### VLESS

- VLESS is the newest protocol of V2Ray and the main difference between VLESS and VMess is that VLESS uses a simplified handshake process to reduce resource usage and increase performance. So it is lightweight and efficient.
- It can operate faster and use less CPU power than other protocols.
- Currently, VLESS does not have built-in encryption, please use it on a reliable channel, such as TLS or REALITY.
- [Learn more](https://xtls.github.io/Xray-docs-next/en/development/protocols/vless.html)

### Trojan (Trojan-GFW)

- Trojan is a proxy server, client and protocol, designed to bypass the Great Firewall of China by imitating HTTPS. Trojan claims to be unidentifiable.
- You can think of Trojan as a simplified version of V2Ray's "WS+TLS" mode, which is faster than V2Ray, more realistic than V2Ray in camouflage, and more difficult to be identified by GFW.
- When a trojan client connects to a server, it first performs a real TLS handshake. If the handshake succeeds, all subsequent traffic will be protected by TLS; otherwise, the server will close the connection immediately as any HTTPS server would.
- Trojan now also supports nginx-like response to plain HTTP requests.
- rojan is designed to operate in correctly configured TLS connections, as it does not provide encryption on its own.
- [Learn more](https://trojan-gfw.github.io/trojan/protocol)

### Trojan-Go

- Compared with the original Trojan, Trojan-Go has some more features, such as multiplexing (smux) to reduce latency, improve concurrent performance, CDN traffic transfer, etc.
- Under normal circumstances, the clients of Trojan and Trojan-Go are universal, and the client of Trojan can be used for the connection of Trojan-Go.
- However, the original Trojan does not support some multiplexing and other functions. If you need to use these functions, you need to use it with a special Trojan-Go client.
- [Learn more](https://p4gefau1t.github.io/trojan-go/advance/customize-protocol-stack/)

### Shadowsocks (Not recommended)

- Shadowsocks is one of the first protocols developped in China specifically to bypass the GFW.
- The shadowsocks protocol is very similar to SOCKS5 but encrypted and simpler.
- It was created in 2012 by a Chinese programmer named "clowwindy", and it's original developper was forced to stop his/her work on the project due to outside pressure. Work on the protocol continues on till this day via various forks on the original project.
- Currently, Burmese operators already have the technology to detect Shadowscocks traffics using Chinese's GFW.
- [Learn more](https://en.wikipedia.org/wiki/Shadowsocks)

### AmneziaWG

- A modern iteration of the popular VPN protocol, AmneziaWG builds upon the foundation set by WireGuard®, retaining its simplified architecture and high-performance capabilities across devices.
- While WireGuard® is known for its efficiency, it had issues with being easily detected due to its distinct packet signatures. AmneziaWG solves this problem by using better obfuscation methods, making its traffic blend in with regular internet traffic. This means that AmneziaWG keeps the fast performance of the original while adding an extra layer of stealth, making it a great choice for those wanting a fast and discreet VPN connection.
- [Learn more](https://docs.amnezia.org/)

### Unrecommended Protocols

The following protocols are not recommended to use. Most traffic analysis systems including GFW can easily recognize them.

- IKEv2
- LTTP/IPSec
- SSTP
- WireGuard
- OpenVPN
