# Setup HAProxy on Debian/Ubuntu

## Step 1 - Install

```bash
sudo apt install -y haproxy
```

## Step 2 - Configure

```bash
# To edit config
sudo nano /etc/haproxy/haproxy.cfg

# To validate config
haproxy -f /etc/haproxy/haproxy.cfg -c

# To restart
sudo systemctl restart haproxy
```

## Example Configs

See [examples](https://github.com/zytx800/vpn-notes/tree/main/haproxy/examples)

## References

- [HAProxy Configuration Basics](https://www.haproxy.com/blog/haproxy-configuration-basics-load-balance-your-servers)
- [HAProxy config tutorials](https://www.haproxy.com/documentation/haproxy-configuration-tutorials/)
- [Introduction to HAProxy ACLs](https://www.haproxy.com/blog/introduction-to-haproxy-acls)
- [HAProxy ACLs](https://www.haproxy.com/documentation/haproxy-configuration-tutorials/core-concepts/acls/)
- [HAProxy SSL Termination](https://www.haproxy.com/blog/haproxy-ssl-termination)
- [HAProxy and Let’s Encrypt](https://www.haproxy.com/blog/haproxy-and-let-s-encrypt)
