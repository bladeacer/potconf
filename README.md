# potconf
My configuration for self-hosting Penpot, a Figma alternative.

If you are seeing this on GitHub, development has moved over to [Codeberg](https://codeberg.org/bladeacer/potconf).

## Setup

Copy files in this repository to `/opt/penpot` with the proper file permissions.

```bash
sudo mkdir -p /opt/penpot
sudo chown root:docker /opt/penpot/
sudo chmod 755 /opt/penpot/
```

```bash
sudo cp penpot.service /opt/penpot/penpot.service
sudo cp penpot.service /opt/penpot/docker-compose.yaml
```

Add this to your `sudo visudo`
```txt
your_user_name ALL=(ALL) NOPASSWD: /usr/bin/systemctl start penpot.service, /usr/bin/systemctl stop penpot.service, /usr/bin/systemctl restart penpot.service, /usr/bin/systemctl status penpot.service
```

## Configuring Systemd service
```bash
sudo cp ./penpot.service /etc/systemd/system/penpot.service

sudo systemctl daemon-reload

sudo systemctl start penpot.service
sudo systemctl enable penpot.service
```

### Checking status
```
sudo systemctl status penpot.service
```

### Updating penpot
```bash
docker compose -f docker-compose.yaml pull
```

## Penpot Desktop
The Penpot Desktop app is recommended for better performance.

[Head over here](https://github.com/author-more/penpot-desktop) for installation instructions.
