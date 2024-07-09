# Setup Marzban on Debian/Ubuntu

## Install

### Step 1 - Install Xray

```bash
sudo bash -c "$(curl -L https://github.com/XTLS/Xray-install/raw/main/install-release.sh)" @ install
```

### Step 2 - Clone repo and prerequisites

```bash
git clone https://github.com/Gozargah/Marzban.git
cd Marzban
sudo python3 -m pip install -r requirements.txt

# Now to build the database
sudo alembic upgrade head

# Create a copy of the .env.example file named .env
cp .env.example .env

# To use marzban-cli, you need to link it to a file in your $PATH
sudo ln -s $(pwd)/marzban-cli.py /usr/bin/marzban-cli
sudo chmod +x /usr/bin/marzban-cli
marzban-cli completion install

# Install the Marzban service in systemctl
sudo chmod +x install_service.sh
sudo ./install_service.sh
# enable and start marzban service
sudo systemctl enable --now marzban.service

# To create a super admin 
marzban-cli admin create --sudo

# To stop marzban service
sudo systemctl stop marzban

# To start marzban service
sudo systemctl start marzban

# To run mazban in non detached mode
# python3 main.py
```

### Step 3 - Edit .env file

```bash
 sudo nano ~/Marzban/.env
```

## References

- [Marzban Docs](https://gozargah.github.io/marzban/en/docs/introduction)
- [Marzban GitHub](https://github.com/gozargah/marzban)
