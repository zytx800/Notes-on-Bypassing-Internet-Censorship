# Setup Marzban on Debian/Ubuntu

## Quick setup

### Step 1 - Install

```bash
sudo bash -c "$(curl -sL https://github.com/Gozargah/Marzban-scripts/raw/master/marzban.sh)" @ install
```

Once the installation is completed, you will see the logs that you can stop watching them by closing the terminal or pressing `Ctrl+C`.

### Step 2 - Setup SSL

(1) In your DNS provider, setup `A` record with your vps server public ip.

(2) Install ACME.sh if not already installed, refer to [ Using ACME.sh](https://github.com/zytx800/Notes-on-Bypassing-Internet-Censorship/tree/main/ssl-certificates#option-2---using-acmesh);

(3) Issue a cert.

```bash
sudo mkdir /var/lib/marzban/certs/<yourdomain>

sudo su
cd ~
~/.acme.sh/acme.sh \
  --issue --force --standalone --days 90 -d <yourdomain> \
  --fullchain-file /var/lib/marzban/certs/<yourdomain>/fullchain.pem \
  --key-file /var/lib/marzban/certs/<yourdomain>/key.pem
exit
```

(4) Update marzban .env file to use SSL cert files.

```bash
sudo nano /opt/marzban/.env

# Uncomment the following lines and update with your cert file paths and then save and exit.
UVICORN_SSL_CERTFILE = "/var/lib/marzban/certs/<yourdomain>/fullchain.pem"
UVICORN_SSL_KEYFILE = "/var/lib/marzban/certs/<yourdomain>/key.pem"
```

### Step 3 - Create admin panel user

```bash
sudo marzban cli admin create --sudo
```

### Step 4 - Restart marzban and access your admin panel

```bash
sudo marzban restart
```

After restarting marzban, you can access admin panel using the following address.

```bash
https://<yourdomain>:8000/dashboard
```

### Step 5 - (Optional) Enable BBR congestion control algorithm

```bash
# Enter sudo access
sudo su

echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf
echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf
sysctl -p

# Exit sudo access
exit
```

### Step 6 - (Optional) Update xray core version

(1) Download and extract xray core.

```bash
# Enter sudo access
sudo su

# Install required packages.
sudo apt install wget unzip

# Create a folder for xray and enter it.
mkdir -p /var/lib/marzban/xray-core && cd /var/lib/marzban/xray-core

# Download the latest version
wget https://github.com/XTLS/xray-core/releases/latest/download/Xray-linux-64.zip

# Unzip the file and delete the compressed file.
unzip Xray-linux-64.zip
rm Xray-linux-64.zip

# Exit sudo access
exit
```

(2) Update marzban .env file to use new xray core.

```bash
sudo nano /opt/marzban/.env

# Uncomment the following lines and update with your xray core file paths and then save and exit.
XRAY_EXECUTABLE_PATH = "/var/lib/marzban/xray-core/xray"
```

(3) Restart marzban.

```bash
sudo marzban restart
```

## Configure xray

(1) Generate a public-private key pair with `./xray x25519` and keep the output.

```bash
cd /var/lib/marzban/xray-core
./xray x25519

#Example of output:
# Private key: M4cZLR81ErNfxnG1fAnNUIATs_UXqe6HR78wINhH7RA
# Public key: ioE61VC3V30U7IdRmQ3bjhOq2ij9tPhVIgAD4JZ4YRY
```

(2) Generate random hex using openssl and keep the output.

```bash
openssl rand -hex 8

#Example of output:
# 9ebafaf9b41e37bc
```

(3) Update and save xray config with the following in the **Core Settings** dialog. To open **Core Settings** dialog, click Settings icon at the top right corner of marzban admin panel.

```jsonc
{
  "log": {
    "loglevel": "warning"
  },
  "inbounds": [
    {
      "tag": "VLESS_TCP_REALITY",
      "listen": "0.0.0.0",
      // Replace port you want
      "port": 10000,
      "protocol": "vless",
      "settings": {
        "clients": [],
        "decryption": "none"
      },
      "streamSettings": {
        "network": "tcp",
        "security": "reality",
        "realitySettings": {
            // Optional. If true, output debugging information.
          "show": false,          
          // Replace camouflage website you want. 
          // The minimum standard of the camouflage website is that it be a foreign website, 
          // support TLSv1.3 and H2, and have a URL that is not redirected elsewhere 
          // (though the apex domain name may be redirected to www).
          "dest": "discordapp.com:443",
          "xver": 0,
          "serverNames": [
            // Replace camouflage website you want.
            "discordapp.com"
          ],
          // Replace the private key with xray x25519 generated output.
          "privateKey": "M4cZLR81ErNfxnG1fAnNUIATs_UXqe6HR78wINhH7RA",
          
          "shortIds": [
            "",
            // Replace the short id with openssl generated output.
            "9ebafaf9b41e37bc"
          ]
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
  ],
  "outbounds": [
    {
      "protocol": "freedom",
      "tag": "DIRECT"
    },
    {
      "protocol": "blackhole",
      "tag": "BLOCK"
    }
  ],
  "routing": {
    "rules": [
      {
        "ip": [
          "geoip:private"
        ],
        "outboundTag": "BLOCK",
        "type": "field"
      }
    ]
  }
}
```

See example [xray configs](https://github.com/zytx800/Notes-on-Bypassing-Internet-Censorship/tree/main/marzban/example-configs).

## References

- [Marzban Docs](https://gozargah.github.io/marzban/en/docs/introduction)
- [Marzban GitHub](https://github.com/gozargah/marzban)
- [Xray REALITY tutorial](https://cscot.pages.dev/2023/03/02/Xray-REALITY-tutorial/)
- [XTLS-Iran-Reality](https://github.com/SasukeFreestyle/XTLS-Iran-Reality)
