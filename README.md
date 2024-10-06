# Fedora Tweaks 🚀💻

This repository contains useful tweaks and tricks for optimizing your Fedora experience.

<br>

<br>

## Speed Up DNF Downloads ⚡
To improve DNF download speeds:
```bash
sudo echo "max_parallel_downloads=10
fastestmirror=True" >> /etc/dnf/dnf.conf
```
This configuration allows for parallel downloads and selects the fastest mirror for quicker package retrieval.

<br>

## Fix VLC Codecs 🎵

To install VLC with required codecs:
```bash
sudo dnf install -y https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm && sudo dnf groupupdate -y multimedia && sudo dnf groupupdate -y sound-and-video && sudo dnf -y install vlc
```
<br>

## Enable Fractional Scaling 📏
To enable fractional scaling:
```bash
gsettings set org.gnome.mutter experimental-features "['scale-monitor-framebuffer']"
```

To disable fractional scaling:
```bash
gsettings set org.gnome.mutter experimental-features "[]"
```

To reset fractional scaling:
```bash
gsettings reset org.gnome.mutter experimental-features
```

<br>

## Increase Volume Beyond 100% 🔊
To allow volume above 100%, run:
```bash
gsettings set org.gnome.desktop.sound allow-volume-above-100-percent 'true'
```

<br>

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

<br>

## GNOME Extensions ✨
App Indicator Support  
**Enable support for app indicators:** [App Indicator](https://extensions.gnome.org/extension/615/appindicator-support)

Desktop Icons  
**Enable desktop icons using the following extension:** [Desktop Icons NG (DING)](https://extensions.gnome.org/extension/2087/desktop-icons-ng-ding)

Clipboard History  
**Add clipboard history support:** [Clipboard History](https://extensions.gnome.org/extension/4839/clipboard-history)

Click to Close Overview  
**Enable clicking to close the overview:** [Click to Close Overview](https://extensions.gnome.org/extension/3826/click-to-close-overview)

Dash to Dock  
**Enable a dock-like application launcher:** [Dash to Dock](https://extensions.gnome.org/extension/307/dash-to-dock)

Show Desktop Button  
**Add a button to show the desktop:** [Show Desktop Button](https://extensions.gnome.org/extension/1194/show-desktop-button)

<br>

# Install Programming Languages & Development Tools 🛠️

## Install Java JDK
```bash
sudo dnf install -y java-latest-openjdk-devel.x86_64
```

## Install NodeJS
```bash
sudo dnf install -y nodejs
```

## Install C++ Development Tools
```bash
sudo dnf group install -y "C Development Tools and Libraries"
sudo dnf group install -y "Development Tools"
sudo dnf install -y cmake
```
