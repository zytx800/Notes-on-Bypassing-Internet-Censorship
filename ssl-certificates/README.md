# SSL Certificates on Debian/Ubuntu

## Option 1 - Using certbot

Step 1 - Install certbot using snapd

```bash
sudo apt install -y snapd
# sudo snap install core
# sudo snap refresh core
sudo snap install certbot --classic
sudo ln -s /snap/bin/certbot /usr/bin/certbot
```

Step 2 - Issue a cert

- **Standalone** (If port 80 is free on server or no web server is running)

```bash
sudo certbot certonly --standalone --agree-tos --non-interactive --email <youremail> -d <yourdomain>

# Or for key-type = rsa:
sudo certbot certonly --standalone --preferred-challenges http --key-type rsa --agree-tos --non-interactive --email <youremail> -d <yourdomain>
```

- **Nginx** webroot plugin

```bash
# (Optional) Create nginx config file
sudo nano /etc/nginx/conf.d/<yourdomain>.conf

# (Optional) And pase the configuration and save:
server {
    listen 80;
    server_name <yourdomain>;
    root /var/www/html/;

    location ~ /.well-known/acme-challenge {
        allow all;
    }
}

#  Create the web root directory.
sudo mkdir -p /var/www/html

# Set www-data (Nginx user) as the owner of the web root.
sudo chown www-data:www-data /var/www/html -R

# Reload Nginx for the changes to take effect.
sudo systemctl reload nginx

# Issue a cert:
sudo certbot --nginx --agree-tos --non-interactive -w /var/www/html/ --email <youremail> -d <yourdomain>
```

Step 3 - Test automatic renewal

```bash
sudo certbot renew --dry-run
```

## Option 2 - Using ACME.sh

Step 1 - Download acme.sh

```bash
sudo apt install -y socat
sudo su
cd ~
curl https://get.acme.sh | sh -s email=<youremail>
exit
```

Step 2 - Issue a cert

- **Standalone** (If port 80 is free on server or no web server is running)

```bash
sudo mkdir /path/to

sudo su
cd ~
~/.acme.sh/acme.sh \
  --issue --force --standalone --days 90 -d <yourdomain> \
  --fullchain-file /path/to/<yourdomain>.crt \
  --key-file /path/to/<yourdomain>.crt.key
exit
```

## For HAProxy

To combine fullchain and key file:

```bash
sudo mkdir /etc/haproxy/certs/

DOMAIN='<yourdomain>' sudo -E bash -c 'cat /etc/letsencrypt/live/$DOMAIN/fullchain.pem /etc/letsencrypt/live/$DOMAIN/privkey.pem > /etc/haproxy/certs/$DOMAIN.pem'

# (Optional) To set permission
# sudo chown haproxy:haproxy /etc/haproxy/certs
# sudo chmod 770 /etc/haproxy/certs
```

## References

- [letsencrypt.org](https://letsencrypt.org/)
- [certbot.eff.org](https://certbot.eff.org/)
- [Certbot commands documentation](https://eff-certbot.readthedocs.io/en/latest/using.html#certbot-commands)
- [ACME.sh GitHub](https://github.com/acmesh-official/acme.sh?tab=readme-ov-file)
