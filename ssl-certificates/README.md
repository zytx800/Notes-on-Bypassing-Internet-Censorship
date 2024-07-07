# SSL Certificates

## Option 1 - Using Let’s Encrypt

Step 1 - Install certbot using snapd

```bash
sudo apt install -y snapd
sudo snap install core
sudo snap refresh core
sudo snap install certbot --classic
sudo ln -s /snap/bin/certbot /usr/bin/certbot
```

Step 2 - Issue a cert

- For Standalone (If port 80 is free and no web server installed)

```bash
sudo certbot certonly --standalone --preferred-challenges http --key-type rsa --agree-tos --email <your-email> -d <your-domain>
```

- For Nginx webroot plugin

```bash
# TODO
```

## Option 2 - Using ACME.sh

Step 1 - Download acme.sh

```bash
sudo apt install -y socat
sudo su
cd ~
curl https://get.acme.sh | sh -s email=<your-email>
exit
```

Step 2 - Issue a cert

- For Standalone (If port 80 is free and no web server installed)

```bash
sudo mkdir /path/to

sudo su
cd ~
~/.acme.sh/acme.sh \
  --issue --force --standalone --days 90 -d <your-domain> \
  --fullchain-file /path/to/<your-domain>.crt \
  --key-file /path/to/<your-domain>.crt.key
exit
```

## References

- [letsencrypt.org](https://letsencrypt.org/)
- [certbot.eff.org](https://certbot.eff.org/)
- [ACME.sh GitHub](https://github.com/acmesh-official/acme.sh?tab=readme-ov-file)
