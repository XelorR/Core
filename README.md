# Core

Elegant and powerful layout for 34 key keyboard

Currently inplemented in [Kanata](https://github.com/jtroo/kanata), but most of the features may be configured with QMK or ZMK keyboards as well.

## Key features and design focus

- Focus on two languages: English and Russian and custom layouts for both
- Modular approash for keyboard layouts - rearrange, plug new, create yours by copypasting existent layouts
- Easy to disable or switch fo qwerty/йцукен in case if you want to share your PC with your grandma
- Focus on 34 key ergonomic split keyboards, but usable on legacy row sraggeeed devices too
- Navigation, Symbol and Numeric layers with strong focus on comfortable positiins - 3x3 home block
- Single symbol layer with same symbol set on the same positions for both languages
- Simple enough to implement most of the features entirely in your keyboard with QMK or ZMK
- Powerful enough to be superuor to QMK Vial implementation
- Home row mods, home row mods everywhere! With separate config for each finger!

## Layers pictures and description

- todo

## How to:

1. Install [Kanata](https://github.com/jtroo/kanata)
2. Clone the repo
3. Arrange your ergo split keyboard keys [as shown in defsrc](main.kbd#L2-L5)
4. Check and select your keyboard layouts in [main.kbd](main.kbd)
5. (Optional) set env variables to adjust language switching, check options in [lang-switching.kbd](lang-switching.kbd). Move row with `(include default-layouts.kbd)` up if you want to use system default layouts (qwerty/йцукен) by some reason.
6. Run main.kbd config with kanata or enable the service and enjoy!
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
