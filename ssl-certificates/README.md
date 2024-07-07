# SSL Certificates

## Option 1 - Using ACME.sh

Step 1 - Install

```bash
sudo apt install -y socat
sudo su
cd ~
curl https://get.acme.sh | sh -s email=<your-email>
exit
```

Step 2 - Issue a cert (Standalone)

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

[ACME.sh GitHub](https://github.com/acmesh-official/acme.sh?tab=readme-ov-file)
