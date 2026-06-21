# Integrative-Project-Deliverables
Integrative Project: Deliverables by Andres Pesantez, Ariel Yumbillo and Israel Farfan
##  Project Description
What is a cubic? Cubic is a aplication to create own distro with some free software aplications, it depends on the person or group.

---
##  ISO Technical Specifications
* **Filename:** `IAAdis-desktop-amd64.iso`
* **Approximate Size:** ~6.04 GiB
* **Base OS:** Ubuntu / Linux Mint (64-bit)
## We need install cubic into our vm with ubuntu or anyone distribution
Use the codes into the cubic repo
![alt text](image.png)
## Then we have the aplication into the virtual box
![alt text](VirtualBox_UnixFinal_20_06_2026_16_23_50-1.png)
---
## Set up cubic
When we have cubic we need a directory where save the info.
![alt text](<Captura de pantalla 2026-06-21 143935.png>)

Also we use a distro like linux mint to clone the distro for own distro.
![alt text](<Captura de pantalla 2026-06-21 143919.png>)

## Integrated Free Software (6-App Ecosystem)

Proprietary, telemetry-heavy, or redundant default applications (such as Firefox, Thunderbird, and Totem) were purged and replaced with the following open-source alternatives:

1. *LibreWolf:* A customizable web browser focused on privacy, security, and data protection by eliminating telemetry.
2. *Audacious:* A lightweight, low-resource audio player engineered for high performance.
3. *MPV:* A powerful, minimalist command-line-driven media player.
4. *Neovim:* A vim-based text editor extensible via Lua, optimized for terminal development.
5. *KeePassXC:* A secure, local, cross-platform password manager to safeguard user credentials.
6. *Clementine:* A modern, feature-rich music player and library organizer for local media management.
![alt text](<Captura de pantalla 2026-06-21 074611.png>)
---

## Commands that we use to install the apps
##  Build Process & Package Management (Cubic CLI)

The customization was executed entirely inside the Cubic virtual environment terminal (`chroot`). The following commands were used to purge default packages, configure external repositories, and install the new software ecosystem:
###  Purging Default & Redundant Applications
To free up space and remove proprietary or telemetry-heavy software, the default browser, mail client, and media players were completely purged:

apt purge -y firefox totem thunderbird rhythmbox
apt autoremove -y

## Add librewolf
apt install -y extrepo && extrepo enable librewolf
apt update
## we use those diferrents apps to modify the distro
apt install -y librewolf audacious mpv neovim keepassxc clementine
## Alias to each app
cat << 'EOF' >> /etc/skel/.bashrc

# --- Lab: Free Software Ecosystem Shortcuts ---

alias web='librewolf'
alias musica='audacious'
alias video='mpv'
alias edit='nvim'
alias ll='ls -la'
alias llaves='keepassxc'
alias biblioteca='clementine'
EOF

#### VirtualBOX with IAA distro

1. Create a new virtual machine with the type set to **Linux** and version to **Ubuntu (64-bit)**.
2. In the hardware section, allocate at least **2 CPU Cores** and **4 GB of RAM**.
3. **Important!** Check the box **"Skip Unattended Installation"**.
4. In the Storage section, mount the `IAAdis-desktop-amd64.iso` file into the virtual optical drive.
5. *(Optional)* If you experience screen flickering or a black screen, change the graphics controller to `VBoxSVGA` under the Display tab and allocate 128 MB of video memory.
6. Start the virtual machine. The system will boot directly into the customized **Live OS** environment.

![alt text](<Captura de pantalla 2026-06-21 152640.png>)

#### END
Finally we have the distro with free software apps
![alt text](<Captura de pantalla 2026-06-21 154221.png>)