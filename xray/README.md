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

## References

- [Xray-install](https://github.com/XTLS/Xray-install)
- [Project X Official Website](https://xtls.github.io/)
- [Xray Config Examples](https://github.com/XTLS/Xray-examples)
