# Setup HAProxy on Debian/Ubuntu

## Step 1 - Install

```bash
sudo apt install -y haproxy
```

## Step 2 - Configure

```bash
# To edit config
nano /etc/haproxy/haproxy.cfg

# To validate config
haproxy -f /etc/haproxy/haproxy.cfg -c

# To restart
sudo systemctl restart haproxy
```
