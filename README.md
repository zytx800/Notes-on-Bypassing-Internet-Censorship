# Notes on Bypassing Internet Censorship in Myanmar

***Last updated: 2024-07-31***

I learned a little about GFW ([Great Firewall of China](https://en.wikipedia.org/wiki/Great_Firewall)) after Myanmar internet service providers installed the GFW liked firewalls and censored some websites and VPNs. Along with learning a little about the GFW, I also learned a little about internet freedom and internet censorship circumvention tools. There are many methods to bypass internet censorship. This repo is focusd on a short notes of what I experienced while building personal vpn platform to bypass internet censorship in Myanmar.

I divide this note into three parts as follows:

1. [Choosing Cloud VPS Providers](#1-choosing-cloud-vps-providers)
2. [Choosing VPN Tools and Protocols](#2-choosing-vpn-tools-and-protocols)
3. [Protocol Notes](#3-protocol-notes)

## 1. Choosing Cloud VPS Providers

Before choosing cloud vps providers, you need to know a little about international bank cards issued by Myanmar banks. Myanmar banks issue **VISA**, **Mastercard**, **JCB** and **UnionPay** cards as international payment cards. Most cloud service providers accept **Debit Card** or **Credit Card** only. **Prepaid Cards (Top-up Cards)** are not accepted by most cloud service providers.

Here are some debit and credit cards that can be used in most cloud service providers and the banks that issue them:

- **AYA Bank**: JCB (Debit & Credit Cards), VISA (Credit Card Only)
- **CB Bank**: JCB (Debit Card Only), VISA (Credit Card Only), Mastercard (Credit Card Only)
- **KBZ Bank**: VISA (Credit Card Only)
- **UAB Bank**: VISA (Credit Card Only)
- **Yoma Bank**: Mastercard (Debit Card Only)

When selecting cloud vps providers, I have listed them in order based on free trial availability, free monthly internet data traffic availability and convenience with bank cards in Myanmar.

### 1.1 Amazon AWS Lightsail (Recommended)

- 3 months free tier available for new customers
- Up to free **3 TB** monthly data traffic to internet when selecting **12 USD / month free trial** plan, see more [data traffic pricing FAQ](https://aws.amazon.com/lightsail/faq/)
- 2 vCPUs, 2 GB RAM, 60GB SSD
- Suport account registration from Myanmar
- Support VISA, Mastercard and JCB debit or credit cards issued by Myanmar's Banks (Note: it doesn't support Prepaid Cards.)
- [AWS Lightsail Website Link](https://aws.amazon.com/free/compute/lightsail/)

### 1.2 Amazon AWS EC2

- 12 months free tier available for new customers
- 1 x t2.micro instance per month in free tier
- Free **100 GB** data traffic monthly to internet, see more [ec2 data traffic pricing](https://aws.amazon.com/ec2/pricing/on-demand/)
- 1 vCPUs, 1 GB RAM and 30GB SSD
- Suport account registration from Myanmar
- Support VISA, Mastercard and JCB debit or credit cards issued by Myanmar's Banks (Note: it doesn't support Prepaid Cards.)
- [AWS EC2 Website Link](https://aws.amazon.com/ec2/)

### 1.3 Microsoft Azure

- Free $200 credit for 12 months for new customers
- Free **100 GB** data traffic monthly to internet, see more [Azure data traffice bandwidth pricing](https://azure.microsoft.com/en-us/pricing/details/bandwidth/)
- ***Azure account registration is currently not supported for Myanmar region***, but VISA credit cards issued by Myanmar's Banks can be used. (Ask your friends who are in a Microsoft Azure supported country to help you sign up)
- [Microsoft Azure Website Link](https://azure.microsoft.com/en-us/free)

### 1.4 Google Cloud Platform

- Free $300 credit for 12 months for new customers
- 1 x ec2-miro instance per month in free tier
- Free **200 GB** data traffic monthly to internet, see more [Google Cloud Network Pricing](https://cloud.google.com/vpc/network-pricing)
- ***GCP account registration is currently not supported for Myanmar region***, but VISA, Mastercard and JCB debit or credit cards issued by Myanmar's Banks can be used. (Ask your friends who are in a GCP supported country to help you sign up)
- [Google Cloud Platform Website Link](https://cloud.google.com/free/)

### 1.5 DigitalOcean (Not Tested)

- $200 free credit for 60 days for new customers
- [DigitalOcean Website Link](https://try.digitalocean.com/freetrialoffer/)

### 1.6 Oracle Cloud Infrastructure  (Not Tested)

- $300 free credit for 30 days for new customers
- [OCI Website Link](https://www.oracle.com/sg/cloud/free/)

### 1.7 VPS Servers with Unlimited Data Transfer Bandwidth

- [JustHost](https://just.hosting/services/vps) - Note: Not tested
- [UltaHost](https://bill.ultahost.com/store/linux-vps-hosting) - Note: Not tested
- [DEVPS](https://bluevps.com/vps-unlimited-bandwidth) - Note: Not tested

## 2. Choosing VPN Tools and Protocols

I choose VPN and Proxy tools base on the followings:

1. Being free and open-source
2. Long-term resistance and better bypass of GFW and other Internet filters
3. Having a client app for Android, iOS, Windows, macOS and Linux platforms
4. Having good speed test results

My suggestion is that when setting up a vpn server, ***you should change your domain name and public ip every 3 or 4 weeks*** because GFW and traffic analyzers may still block your domains and IPs based on usage after a period of time.

### 2.1 Xray (Recommended)

Xray is completely similar to V2Ray, and Xray is the core module of [Project X](https://xtls.github.io/en/).

Since rprx, the author of Xray and XTLS, was once an important member of the V2fly community, Xray directly forked all V2Ray functions, optimized performance, added new functions, and created the original VLESS and XTLS protocols, making Xray a superset of V2Ray in terms of functionality and fully compatible with V2Ray.

In short, Xray is a branch of V2Ray and Xray is a superset of V2Ray.

Xray XTLS protocol aims to enhance communication efficiency and allows Xray to work at a faster speed.

XTLS, one of Xray’s key features, is an improvement over V2Ray’s WS TLS protocol which is less optimized for communication over the internet.

Xray also features a powerful routing system that is highly customizable.

Learn more about Xray on [Project X Official Website](https://xtls.github.io/en/).

#### Xray server-side setup

- [Install Xray Core on Debian/Ubuntu](https://github.com/zytx800/Notes-on-Bypassing-Internet-Censorship/tree/main/xray)
- [Hiddify Manager Setup](https://hiddify.com/manager/installation-and-setup/How-to-install-different-versions-of-Hiddify-Manager/) - (Xray Core + User Management Admin Web Panel - My Preferred Method)
- [Marzban Web Panel Setup](https://github.com/Gozargah/Marzban) - (Xray Core + User Management Admin Web Panel)

#### Xray client apps

##### Android apps

- [Hiddify - Download from Play Store](https://play.google.com/store/apps/details?id=app.hiddify.com) / [GitHub repo](https://github.com/hiddify/hiddify-next)  (My Preferred Andorid App)
- [v2rayNG - Download from Play Store](https://play.google.com/store/apps/details?id=com.v2ray.ang) / [GitHub repo](https://github.com/2dust/v2rayNG)

##### iOS apps

- [FoXray - Download from App Store](https://apps.apple.com/us/app/foxray/id6448898396) (Note: Free, not open-source - My Preferred iOS App)
- [V2Box - Download from App Store](https://apps.apple.com/us/app/v2box-v2ray-client/id6446814690)  (Note: Free, not open-source, contains Ads)
- [Streisand - Download from App Store](https://apps.apple.com/us/app/streisand/id6450534064) (Note: Free, not open-source, contains Ads)

##### Windows apps

- [Hiddify - Download form Microsoft Store](https://apps.microsoft.com/detail/9pdfnl3qv2s5?hl=en-us&gl=SG) / [GitHub repo](https://github.com/hiddify/hiddify-next) (My Preferred Windows App)
- [v2rayN - Download from GitHub release](https://github.com/2dust/v2rayN/releases)
- [Qv2ray - Download from GitHub release](https://github.com/Qv2ray/Qv2ray/releases) (Note: Only a few procols are supported)
- [Furious - Download from GitHub release](https://github.com/LorenEteval/Furious/releases) (Note: Not tested)

##### macOS apps

- [Hiddify - Download from GitHub release](https://github.com/hiddify/hiddify-next/releases)  (Note: Not tested)
- [V2RayXS - Download from GitHub release](https://github.com/tzmax/V2RayXS/releases) (Note: Not tested)
- [Furious - Download from GitHub release](https://github.com/LorenEteval/Furious/releases) (Note: Not tested)
- [Qv2ray - Download from GitHub release](https://github.com/Qv2ray/Qv2ray/releases) (Note: Not tested)
- [FoXray - Download from App Store](https://apps.apple.com/us/app/foxray/id6448898396) (Note: Not tested)

##### Linux apps

- [Hiddify - Download from GitHub release](https://github.com/hiddify/hiddify-next/releases)  (Note: Not tested)
- [v2rayA - Download from GitHub release](https://github.com/v2rayA/v2rayA/releases/) - (Note: Not tested)
- [nekoray - Download from GitHub release](https://github.com/MatsuriDayo/nekoray/releases)  - (Note: Not tested)
- [Furious - Download from GitHub release](https://github.com/LorenEteval/Furious/releases) (Note: Not tested)

#### Recommended Protocols to use with Xray

- VLESS (with TLS or REALITY security)
- Trojan (with TLS security)

### 2.2 Amnezia VPN

Amnezia VPN is a free and open-source application that allows users to create a personal VPN using their own server.

Amnezia VPN is a project by [Internet activists](https://en.wikipedia.org/wiki/Internet_activism) from Russia, who are searching for solutions to resist state censorship.

Amnezia introduced its own **AmneziaWG** protocol, a latest addition, which is an improved version of a popular WireGuard protocol and was designed to be used in the world’s harshest internet climates.

Learn more about [Amnezia - Official Website](https://amnezia.org/en)

#### Installing Amnezia VPN on your own Server

[See Amnezia Docs](https://docs.amnezia.org/documentation/instructions/install-vpn-on-server)

#### Amnezia client apps

##### Android apps

- [Amnezia VPN - Download from Play Store](https://play.google.com/store/apps/details?id=org.amnezia.vpn)

##### iOS apps

- [AmneziaVPN - Download from App Store](https://apps.apple.com/us/app/amneziavpn/id1600529900)

##### Windows apps

- [AmneziaVPN - Download from GitHub Release](https://github.com/amnezia-vpn/amnezia-client/releases)

##### macOS apps

- [AmneziaVPN - Download from GitHub Release](https://github.com/amnezia-vpn/amnezia-client/releases)

##### Linux apps

- [AmneziaVPN - Download from GitHub Release](https://github.com/amnezia-vpn/amnezia-client/releases)

#### Recommended Protocols to use with Amazia VPN

- AmneziaWG

### 2.3 SoftEther (Recommended for Windows Users)

SoftEther VPN is free open-source, cross-platform, multi-protocol VPN client and VPN server software, developed as part of Daiyuu Nobori's master's thesis research at the University of Tsukuba.

VPN protocols such as SSL-VPN (HTTPS), L2TP/IPsec, OpenVPN, and Microsoft Secure Socket Tunneling Protocol are provided in a single VPN server. Among those protocols, SoftEther's SSL-VPN (HTTPS) is currently resistant to GFW's filters (Tested with MPT FTTH, ATOM FTTH).

Learn more about SoftEther on [SoftEther Official Website](https://www.softether.org/)

***Note: I recommend SoftEther for Windows users with SSL-VPN (HTTPS) connection only.***

#### SoftEther server-side setup

[Setup SoftEther VPN Server on Debian/Ubuntu](https://github.com/zytx800/Notes-on-Bypassing-Internet-Censorship/tree/main/softether)

#### SoftEther client apps

##### Windows apps

- [Download SoftEtherVPN client for Windows from GitHub releases](https://github.com/SoftEtherVPN/SoftEtherVPN/releases)

#### Recommended Protocols to use with SoftEther VPN

- SSL-VPN (HTTPS) connection

### 2.4 Sing-box (Not Tested)

It is an alternative to V2Ray and Xray and it can be used with various V2Ray/Xray clients.

Sing-box is designed to focus on performance, lightweight design, usability, modularity, and code quality.

In addition to supporting shadowsocks, trojan, vmess, vless and socks protocols, it also supports newer protocols like ShadowTLS, Hysteria, and NaiveProxy.

For transport, it can be used with V2Ray transport options such as TCP, WebSocket, QUIC, and gRPC.

Learn more sing-box on [Sing-box Official Website](https://sing-box.sagernet.org/)

### 2.5 V2Ray

As the core part of [Project V](https://www.v2ray.com/), V2Ray is a tool that provides a secure platform for making private networks.

V2Ray was developed in 2015 as an alternative to Shadowsocks.

V2Ray is a powerful proxy platform that supports a variety of protocols, among them, only the VMess protocol is an exclusive encrypted commnunication protocol originally created by the V2Ray community.

V2Ray currently supports Blackhole, Dodkodemo-door, Freedom, HTTP, MTProto, Shadowsocks, Socks and VMess protocols.

As of December 2019, V2Ray's optional transport layer configurations are: TCP, mKCP, WebSocket, HTTP/2, DomainSocket, QUIC. Among them, mKCP, QUIC and TCP are used to optimize network quality, WebSocket is used for camouflage, HTTP/2 and DomainSocket are used for transmission and TLS encryption.

Learn more about V2Ray on [Project V Official Website](https://www.v2ray.com/en/)

### 2.6 Others

- [OpenVPN](https://openvpn.net/) (Don't use it) - Most traffic analysis systems and GFW can easily recognize OpenVPN protocol and will block it.

- [Outline VPN](https://getoutline.org/) (Not Recommended) - Outline vpn server uses Shadowsocks protocol. I tried Outline vpn with MPT FTTH, it got blocked after a few hours of use.

## 3. Protocol Notes

### 3.1 VMess

VMess is a encrypted transmission protocol dedicated to V2Ray.

VMess is a TCP-based protocol, and all data is transmitted using TCP.

VMess is a stateless protocol, which means that data can be transmitted directly between the client and the server without the need for a handshake. Each data transmission has no impact on other data transmissions before or after it.

When a VMess client initiates a request, the server checks whether the request comes from a legitimate client. If the validation passes, the server forwards the request and sends the obtained response back to the client.

VMess uses an asymmetric format, meaning that the requests sent by the client and the responses from the server use different formats.

It is divided into inbound and outbound parts, and usually used as a bridge between th V2Ray client and the server.

Because of the added obfuscation and encryption, it is said to be safer than Shadowsocks and more difficult for censors to detect VPN  activity as it seems like regular Internet traffic.

[Learn more about VMess](https://xtls.github.io/en/development/protocols/vmess.html)

### 3.2 VLESS (Recommended)

VLESS is the newest protocol of V2Ray and the main difference between VLESS and VMess is that VLESS uses a simplified handshake process to reduce resource usage and increase performance. So it is lightweight and efficient.

It can operate faster and use less CPU power than other protocols.

Currently, VLESS does not have built-in encryption, please use it on a reliable channel, such as TLS or REALITY.

[Learn more about VLESS](https://xtls.github.io/Xray-docs-next/en/development/protocols/vless.html)

### 3.3 Trojan (Trojan-GFW)

Trojan is a proxy server, client and protocol, designed to bypass the Great Firewall of China by imitating HTTPS. Trojan claims to be unidentifiable.

You can think of Trojan as a simplified version of V2Ray's "WS+TLS" mode, which is faster than V2Ray, more realistic than V2Ray in camouflage, and more difficult to be identified by GFW.

When a trojan client connects to a server, it first performs a real TLS handshake. If the handshake succeeds, all subsequent traffic will be protected by TLS; otherwise, the server will close the connection immediately as any HTTPS server would.

Trojan now also supports nginx-like response to plain HTTP requests.

Trojan is designed to operate in correctly configured TLS connections, as it does not provide encryption on its own.

[Learn more about Trojan-GFW](https://trojan-gfw.github.io/trojan/protocol)

### 3.4 Trojan-Go

Compared with the original Trojan, Trojan-Go has some more features, such as multiplexing (smux) to reduce latency, improve concurrent performance, CDN traffic transfer, etc.

Under normal circumstances, the clients of Trojan and Trojan-Go are universal, and the client of Trojan can be used for the connection of Trojan-Go.

However, the original Trojan does not support some multiplexing and other functions. If you need to use these functions, you need to use it with a special Trojan-Go client.

[Learn more about Trojan-Go](https://p4gefau1t.github.io/trojan-go/advance/customize-protocol-stack/)

### 3.5 Shadowsocks (Not recommended)

Shadowsocks is one of the first protocols developped in China specifically to bypass the GFW.

The shadowsocks protocol is very similar to SOCKS5 but encrypted and simpler.

It was created in 2012 by a Chinese programmer named "clowwindy", and it's original developper was forced to stop his/her work on the project due to outside pressure. Work on the protocol continues on till this day via various forks on the original project.

Currently, Burmese operators already have the technology to detect Shadowscocks traffics using Chinese's GFW.

[Learn more about Shadowsocks](https://en.wikipedia.org/wiki/Shadowsocks)

### 3.6 AmneziaWG

AmneziaWG is built upon the foundation set by WireGuard®, retaining its simplified architecture and high-performance capabilities across devices.

While WireGuard® is known for its efficiency, it had issues with being easily detected due to its distinct packet signatures. AmneziaWG solves this problem by using better obfuscation methods, making its traffic blend in with regular internet traffic. This means that AmneziaWG keeps the fast performance of the original while adding an extra layer of stealth, making it a great choice for those wanting a fast and discreet VPN connection.

[Learn more about Amnezia VPN](https://docs.amnezia.org/)

### 3.7 Unrecommended Protocols

The following protocols are not recommended to use. Most traffic analysis systems including GFW can easily recognize them.

- IKEv2
- LTTP/IPSec
- SSTP
- WireGuard
- OpenVPN
