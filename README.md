# Fedora Tweaks 🚀💻

This repository contains useful tweaks and tricks for optimizing your Fedora experience.

## Fix VLC Codecs 🎵

To install VLC with required codecs, run:
```bash
sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm && sudo dnf groupupdate multimedia --setop="install_weak_deps=False" --exclude=PackageKit-gstreamer-plugin && sudo dnf groupupdate sound-and-video
```

## Enable Fractional Scaling 📏
To enable fractional scaling, use:
```bash
gsettings set org.gnome.mutter experimental-features "['scale-monitor-framebuffer']"
```

To disable it:
```bash
gsettings set org.gnome.mutter experimental-features "[]"
```

To reset:
```bash
gsettings reset org.gnome.mutter experimental-features
```

## Increase Volume Beyond 100% 🔊
To allow volume above 100%, run:
```bash
gsettings set org.gnome.desktop.sound allow-volume-above-100-percent 'true'
```

## Remove Unwanted Bloatware ❌
To remove some pre-installed software, use:
```bash
sudo dnf erase yelp
sudo dnf erase totem
sudo dnf erase rhythmbox
sudo dnf erase gnome-tour
sudo dnf erase gnome-maps
sudo dnf erase gnome-boxes
sudo dnf erase mediawriter
sudo dnf erase simple-scan
```