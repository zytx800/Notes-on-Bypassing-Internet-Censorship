# Install Xray Core on Debian/Ubuntu

## Option 1 - Quick Install

```bash
sudo bash -c "$(curl -L https://github.com/XTLS/Xray-install/raw/main/install-release.sh)" @ install
```

## Option 2 - Manual Download

```bash
# Go to target folder
# cd path/to

# Download latest release
curl -s https://api.github.com/repos/XTLS/Xray-core/releases/latest | sed 's/[()",{}]/ /g; s/ /\n/g' | grep "https.*releases/download.*/*.Xray-linux-64\.zip$" | wget -qi -

# Extract
sudo unzip Xray-linux-64.zip
sudo rm Xray-linux-64.zip
```

## References

- [Xray-install](https://github.com/XTLS/Xray-install)
- [Project X Official Website](https://xtls.github.io/)
