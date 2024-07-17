# Setup Xray Core

## Step 1 - Setup Xray Core on Debian/Ubuntu

Skip this step if you are using [Admin Web Panels](#step-2---xray-core-with-user-management-web-admin-panels).

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

### Enable and start service if using install script

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

### Xray config location if using install script

```bash
sudo nano /usr/local/etc/xray/config.json
```

### Xray useful commands

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

## Step 2 - (Optional) Xray Core with User Management Web Admin Panels

- [Hiddify Manager](https://github.com/hiddify/Hiddify-Manager)
- [Marzban](https://github.com/Gozargah/Marzban) / [Setup Marzban on Debian/Ubuntu](https://github.com/zytx800/Notes-on-Bypassing-Internet-Censorship/tree/main/marzban)
- [X-UI English](https://github.com/NidukaAkalanka/x-ui-english)
- [Libertea](https://github.com/VZiChoushaDui/Libertea)

## Step 3 - (Optional) Proxy Servers / Load Balancers

- [Setup HAProxy on Debian/Ubuntu](https://github.com/zytx800/Notes-on-Bypassing-Internet-Censorship/tree/main/haproxy)

## Step 4 - (Optional) Install SSL Certificate

- [Install SSL Certificates on Debian/Ubuntu](https://github.com/zytx800/Notes-on-Bypassing-Internet-Censorship/tree/main/ssl-certificates)

## References

- [Xray-install](https://github.com/XTLS/Xray-install)
- [Project X Official Website](https://xtls.github.io/)
- [Xray Config Examples](https://github.com/XTLS/Xray-examples)
