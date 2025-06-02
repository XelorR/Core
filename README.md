# Core

Elegant and powerful layout for 34 key keyboard

## To describe layers and approach

- For now, just go through [main.kbd](main.kbd) and all it's includes

## Example Systemd service

Create file:

```bash
sudo nano /etc/systemd/system/kanata.service
```

Ensure specifying path to your config folder:

```
[Unit]
Description=Kanata Keyboard Remapping Service
After=network.target

[Service]
Environment=LANG_MODE=SEPARATE
ExecStart=/usr/bin/kanata -c /home/user/Documents/Core/main.kbd
Restart=always
User=root

[Install]
WantedBy=multi-user.target
```

Enable and start:

```bash
sudo systemctl daemon-reload
sudo systemctl enable --now kanata.service
```

View log real time:

```bash
journalctl -u kanata.service -f
```
