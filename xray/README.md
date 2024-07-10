# Install Xray Core on Debian/Ubuntu

## Install

### Option 1 - Quick Install

```bash
sudo bash -c "$(curl -L https://github.com/XTLS/Xray-install/raw/main/install-release.sh)" @ install
```

### Option 2 - Manual Download

```bash
# Check linux operating system and architecture
uname -m

# Go to target folder
cd path/to

# Download latest release
curl -s https://api.github.com/repos/XTLS/Xray-core/releases/latest | sed 's/[()",{}]/ /g; s/ /\n/g' | grep "https.*releases/download.*/*.Xray-linux-64\.zip$" | wget -qi -

# Extract
# sudo apt install -y unzip
sudo unzip Xray-linux-64.zip
sudo rm Xray-linux-64.zip
```

## Enable and start service if using install script

```bash
# Enable
systemctl enable xray

# To start
systemctl start xray

# To stop
systemctl stop xray

# To restart
systemctl restart xray

# View status
systemctl status xray
q #To quit
```

## Xray config location if using install script

```bash
sudo nano /usr/local/etc/xray/config.json
```

## Xray useful commands

```bash
# Go to xray-core directory and
./xray -h

# To generate uuid
./xray uuid

# To generate public and private key pairs for reality.
./xray x25519

# To generate random 16bit hex 
openssl rand -hex 8
```

## Web Admin Panels

- [Marzban](https://github.com/Gozargah/Marzban) / [Setup Marzban on Debian/Ubuntu](https://github.com/zytx800/Notes-on-Bypassing-Internet-Censorship/tree/main/marzban)
- [Hiddify Manager](https://github.com/hiddify/Hiddify-Manager)
- [X-UI English](https://github.com/NidukaAkalanka/x-ui-english)
- [Libertea](https://github.com/VZiChoushaDui/Libertea)

## HAProxy

- [Setup HAProxy on Debian/Ubuntu](https://github.com/zytx800/Notes-on-Bypassing-Internet-Censorship/tree/main/haproxy)

## SSL

- [Install SSL Certificates on Debian/Ubuntu](https://github.com/zytx800/Notes-on-Bypassing-Internet-Censorship/tree/main/ssl-certificates)

## Client apps

### Android apps

- [v2rayNG - Android - Download from Play Store](https://play.google.com/store/apps/details?id=com.v2ray.ang)
- [Hiddify - Android - Download from Play Store](https://play.google.com/store/apps/details?id=app.hiddify.com)
- [V2Box  - Android - Download from Play Store](https://play.google.com/store/apps/details?id=dev.hexasoftware.v2box&hl=en_SG)

### iOS apps

- [FoXray  - iOS - Download from App Store](https://apps.apple.com/us/app/foxray/id6448898396)
- [V2Box - iOS - Download from App Store](https://apps.apple.com/us/app/v2box-v2ray-client/id6446814690)
- [Streisand - iOS - Download from App Store](https://apps.apple.com/us/app/streisand/id6450534064)

### Windows apps

- [Hiddify](https://apps.microsoft.com/detail/9pdfnl3qv2s5?hl=en-us&gl=SG)
- [v2rayN](https://github.com/2dust/v2rayN/releases)
- [Qv2ray](https://github.com/Qv2ray/Qv2ray/releases)
- [nekoray](https://github.com/Matsuridayo/nekoray)
- [Furious](https://github.com/LorenEteval/Furious)
- [InvisibleMan-XRayClient](https://github.com/InvisibleManVPN/InvisibleMan-XRayClient)

### macOS (arm64 & x64)

- [FoXray](https://apps.apple.com/us/app/foxray/id6448898396)
- [V2RayXS](https://github.com/tzmax/V2RayXS/releases)
- [Furious](https://github.com/LorenEteval/Furious)
- [Qv2ray](https://github.com/Qv2ray/Qv2ray/releases)

### Linux apps

- [v2rayA](https://github.com/v2rayA/v2rayA)
- [nekoray](https://github.com/Matsuridayo/nekoray)
- [Furious](https://github.com/LorenEteval/Furious)


## Others that support VLESS, XTLS, REALITY, XUDP, PLUX

- [sing-box](https://github.com/SagerNet/sing-box)

## References

- [Xray-install](https://github.com/XTLS/Xray-install)
- [Project X Official Website](https://xtls.github.io/)
- [Xray Config Examples](https://github.com/XTLS/Xray-examples)
