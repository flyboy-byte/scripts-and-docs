# field-mode

Battery-saving toggle for LXQt field use — ham radio logging, outdoor work, anywhere you're off AC.

One command flips CPU governor, WiFi power save, screen brightness, and TLP battery profile all at once. Toggle it off to restore everything.

## Usage

```bash
field-mode          # toggle on/off
field-mode on
field-mode off
field-mode status
```

## What it does

| Setting | Field mode ON | Field mode OFF |
|---|---|---|
| CPU governor | `powersave` | `schedutil` |
| WiFi power save | on | off |
| Screen brightness | 40% | restored to previous |
| TLP profile | forced battery | auto-detect |

## Setup

**Dependencies:**
```bash
sudo pacman -S tlp brightnessctl
sudo systemctl enable --now tlp
```

**Install the script:**
```bash
cp field-mode ~/bin/field-mode
chmod +x ~/bin/field-mode
# make sure ~/bin is in your PATH
echo 'export PATH="$HOME/bin:$PATH"' >> ~/.zshrc
```

**Passwordless sudo** (so it doesn't prompt mid-field):
```bash
# edit sudoers.example — replace "logan" with your username
sudo visudo -c -f sudoers.example && sudo cp sudoers.example /etc/sudoers.d/field-mode
```

**LXQt keyboard shortcut:**
LXQt Settings → Shortcut Keys → Add → command `field-mode`, assign a key like `Meta+F`.
