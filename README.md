# Core

Elegant and powerful layout for 34 key keyboard

## Layers pictures and description

- todo

## How to:

1. Install [Kanata](https://github.com/jtroo/kanata)
2. Clone the repo
3. Arrange your ergo split keyboard keys [as shown in defsrc](main.kbd#L2-L5)
4. Check and select your keyboard layouts in [main.kbd](main.kbd)
5. (Optional) set env variables to adjust language switching, check options in [lang-switching.kbd](lang-switching.kbd)
6. Run or enable service and enjoy!
7. (Optional) you can still use it on legacy row staggered keyboard, using space and right alt as main thumb keys

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
