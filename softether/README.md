# Setup SoftEther VPN Server on Debian/Ubuntu

## Setup SoftEther DE

### Step 1 - Install requirements

```bash
sudo apt -y install cmake gcc g++ make pkgconf libncurses5-dev libssl-dev libsodium-dev libreadline-dev zlib1g-dev
```

### Step 2 - Build source code and install

```bash
git clone https://github.com/SoftEtherVPN/SoftEtherVPN.git
cd SoftEtherVPN
git submodule init && git submodule update
./configure
make -C build

# (Optional) To install
sudo make -C build install
```

Or, to downalod the latest release:

```bash
# Download SoftEtherVPN latest release:
curl -s https://api.github.com/repos/SoftEtherVPN/SoftEtherVPN/releases/latest | sed 's/[()",{}]/ /g; s/ /\n/g' | grep "https.*releases/download.*/*.tar\.xz$" | wget -qi - -O - | tar -Jxf - --transform 's:^[^/]*:SoftEtherVPN:'
```

### Step 3 - Create service startup files

```bash
sudo wget -P /opt/ https://raw.githubusercontent.com/zytx800/vpn-notes/main/softether/softether-vpnserver.sh
sudo wget -P /etc/systemd/system/ https://raw.githubusercontent.com/zytx800/vpn-notes/main/softether/softether-vpnserver.service
sudo chmod 755 /opt/softether-vpnserver.sh
sudo systemctl enable softether-vpnserver
sudo systemctl start softether-vpnserver
```

### Step 4 - Configure vpn server (Initial)

```bash
sudo vpncmd

# Enter 1 - Management of VPN Server or VPN Bridge
# Enter 127.0.0.1:5555 - When prompted Hostname of IP address of destination
# Enter <empty> or DEFAULT - When prompted Virtual Hub Name

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

### Step 5 - Configure vpn server (Advanced)

```bash
sudo vpncmd 127.0.0.1:5555

# To get List of TCP Listeners
ListenerList

# To stop listening on tcp port 443 and 1194
ListenerDisable 443
ListenerDisable 1194

# To delete listening tcp port 443 and 1194
ListenerDelete 443
ListenerDelete 1194

# To list the UDP ports that the server is listening on
PortsUDPGet

# To set the UDP ports that the server should listen on
PortsUDPSet

# To exit
exit
```

### Step 6 - Set a SSL certificate

To issue a cert see [SSL Certificates section](https://github.com/zytx800/vpn-notes/tree/main/ssl-certificates)

To set a cert

```bash
sudo vpncmd 127.0.0.1:5555

ServerCertSet
# Enter fullchain and private key file paths
```

## Step 7 - (Optional) HAProxy

- [Setup HAProxy on Debian/Ubuntu](https://github.com/zytx800/Notes-on-Bypassing-Internet-Censorship/tree/main/haproxy)


### Step 8 - Download SoftEther VPN client for Windows

[Download SoftEtherVPN client for Windows from GitHub releases](https://github.com/SoftEtherVPN/SoftEtherVPN/releases)

Or, build SoftEther VPN for Windows from source:
[Build SoftEther VPN for Windows](https://github.com/SoftEtherVPN/SoftEtherVPN/blob/master/src/BUILD_WINDOWS.md)

## References

- [SoftEtherVPN GitHub - BUILD_UNIX](https://github.com/SoftEtherVPN/SoftEtherVPN/blob/master/src/BUILD_UNIX.md)
