# Setup SoftEther on Debian/Ubuntu

## Setup SoftEther DE from source

### Step 1 - Install requirements

```bash
sudo apt -y install cmake gcc g++ make pkgconf libncurses5-dev libssl-dev libsodium-dev libreadline-dev zlib1g-dev
```

### Step 2 - Build from source code and install

```bash
git clone https://github.com/SoftEtherVPN/SoftEtherVPN.git
cd SoftEtherVPN
git submodule init && git submodule update
./configure
make -C build
sudo make -C build install
```

### Step 3 - Creating service startup files

```bash
sudo wget -P /opt/ https://raw.githubusercontent.com/zytx800/vpn-notes/main/softether/softether-vpnserver.sh
sudo wget -P /etc/systemd/system/ https://raw.githubusercontent.com/zytx800/vpn-notes/main/softether/softether-vpnserver.service
sudo chmod 755 /opt/softether-vpnserver.sh
sudo systemctl enable softether-vpnserver
sudo systemctl start softether-vpnserver
```

### Step 4 - Configure SoftEther vpn server

```bash
sudo vpncmd

# Enter 1 - Management of VPN Server or VPN Bridge
# Enter 127.0.0.1:5555 - when prompted Hostname of IP address of destination
# Enter <empty> - when prompted Virtual Hub Name

# To set server password
ServerPasswordSet

# To create a hub named VPN
HubCreate VPN

# Enable secure NAT on hub VPN
Hub VPN
SecureNatEnable

# To exit
exit
```

## References

[SoftEtherVPN GitHub](https://github.com/SoftEtherVPN/SoftEtherVPN/blob/master/src/BUILD_UNIX.md)
