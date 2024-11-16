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

## Clean system logs ♻️
To clean system logs:
```bash
sudo journalctl --rotate
sudo journalctl --vacuum-time=1s
```

<br>

## Clean Old Kernels ♻️
To clean old kernels:
```bash
sudo dnf -y install --setopt installonly_limit=1 kernel
```

<br>

## Fix VLC Codecs 🎵

To install VLC with required codecs:
```bash
sudo dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm && sudo dnf install https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm && sudo dnf install @sound-and-video && sudo dnf install @multimedia && sudo dnf -y install vlc
```

To fix codecs error:
```bash
sudo dnf install ffmpeg libavcodec-freeworld --allowerasingUpdate README.md
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
**App Indicator Support**  
Enable support for app indicators: [App Indicator](https://extensions.gnome.org/extension/615/appindicator-support)

**Desktop Icons**  
Enable desktop icons using the following extension: [Desktop Icons NG (DING)](https://extensions.gnome.org/extension/2087/desktop-icons-ng-ding)

**Clipboard History**  
Add clipboard history support: [Clipboard History](https://extensions.gnome.org/extension/4839/clipboard-history)

**Click to Close Overview**  
Enable clicking to close the overview: [Click to Close Overview](https://extensions.gnome.org/extension/3826/click-to-close-overview)

**Dash to Dock**  
Enable a dock-like application launcher: [Dash to Dock](https://extensions.gnome.org/extension/307/dash-to-dock)

**Show Desktop Button**  
Add a button to show the desktop: [Show Desktop Button](https://extensions.gnome.org/extension/1194/show-desktop-button)

<br>

# Install OBS
To install OBS:
```bash
sudo dnf install obs-studio
```

To install Intel QSV Decoder for OBS:
```bash
sudo dnf install intel-media-driver
```

# Install Brave
Create a repository file for Brave:

```bash
sudo nano /etc/yum.repos.d/brave-browser.repo
```

Paste the following content into the file and Save:
```text
[brave]
name=Brave Browser
baseurl=https://brave-browser-rpm-release.s3.brave.com/x86_64/
gpgcheck=1
gpgkey=https://brave-browser-rpm-release.s3.brave.com/brave-core.asc
enabled=1
```

Install Brave
```bash
sudo rpm --import https://brave-browser-rpm-release.s3.brave.com/brave-core.asc
sudo dnf install brave-browser
```

# Install Programming Languages & Development Tools 🛠️

## Install Java JDK
```bash
sudo dnf install -y java-latest-openjdk-devel.x86_64
```

To change Java Alternative:
```bash
sudo alternatives --config java
```

## Install NodeJS
```bash
sudo dnf install -y nodejs
```

## Install C++ Development Tools
```bash
sudo dnf install @development-tools 
sudo dnf install -y cmake
```

## Install MongoDB 🍃
To install MongoDB on Fedora 41 and resolve potential OpenSSL issues, follow these steps:

Step 1: Remove Existing MongoDB Installations ❌
If you've previously installed MongoDB, remove any existing packages or repositories to avoid conflicts:

```bash
sudo systemctl stop mongod
sudo dnf erase $(rpm -qa | grep mongo)
sudo rpm -e mongodb-org mongodb-mongosh
sudo rm -rf /var/log/mongodb /var/lib/mongo
sudo rm -f /etc/yum.repos.d/mongodb-org-*.repo
```

Step 2: Add MongoDB 8.0 Repository 📦
Create a repository file for MongoDB 8.0:

```bash
sudo nano /etc/yum.repos.d/mongodb-org-8.0.repo
```

Paste the following content into the file:
```text
[mongodb-org-8.0]
name=MongoDB Repository
baseurl=https://repo.mongodb.org/yum/redhat/9/mongodb-org/8.0/x86_64/
gpgcheck=1
enabled=1
gpgkey=https://pgp.mongodb.com/server-8.0.asc
```
Save and close the file.

Step 3: Install MongoDB with OpenSSL 3 Support 🔐
To install MongoDB with the correct OpenSSL 3 support, use the following command:

```bash
sudo dnf install -y mongodb-org mongodb-mongosh-shared-openssl3
```

Step 4: Start MongoDB Service 🚀
After installation, start the MongoDB service:

```bash
sudo systemctl start mongod
```

Step 5: Verify Installation ✅
Check if MongoDB is running properly:

```bash
sudo systemctl status mongod
```
This should resolve any OpenSSL-related issues and allow MongoDB to function smoothly on Fedora 40.
