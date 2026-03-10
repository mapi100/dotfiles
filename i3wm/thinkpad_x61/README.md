# Debian Setup

This repository contains the packages and configuration needed to reproduce my Debian i3wm environment.

## Install packages

```bash
sudo apt update
xargs -a packages.txt sudo apt install -y
```

## Keyboard Layout Toggle (EN / ES)

Create a script to toggle the keyboard layout between **English (US)** and **Spanish (Latin American)**.

### 1. Create the script

```bash
nano ~/.config/i3/toggle-kb.sh
```

Paste the following:

```bash
#!/bin/sh

current="$(setxkbmap -query | awk '/layout/ {print $2}')"

case "$current" in
    us)
        setxkbmap -layout latam
        ;;
    *)
        setxkbmap -layout us
        ;;
esac
```

Make the script executable:

```bash
chmod +x ~/.config/i3/toggle-kb.sh
```

Add this line to i3 config:

```bash
bindsym $mod+m exec --no-startup-id ~/.config/i3/toggle-kb.sh
```


