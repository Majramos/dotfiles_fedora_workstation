# My configuration files
- Fedora 41 Workstation
- Asus VivoBook\_ASUSLaptop X580GD\_N580GD

## Change hostname

```bash
$ sudo hostnamectl set-hostname "fedora-asus"
```

## Speed up dnf
append to `dnf.conf`: *max_parallel_downloads=10*
```bash
$ echo 'max_parallel_downloads=10' | sudo tee -a /etc/dnf/dnf.conf
```

## Enable Flathub
```bash
$ flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```

## Setup git default branch name
```bash
$ git config --global init.defaultBranch main
```

## Setup dotfiles repos

based on guide by [Atlassian](https://www.atlassian.com/git/tutorials/dotfiles)

```bash
git init --bare $HOME/.dotfiles
alias config='/usr/bin/git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'
config config --local status.showUntrackedFiles no
echo "alias config='/usr/bin/git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'" >> $HOME/.bashrc.d/alias

config remote add origin git@gitlab.com:majramos/dotfiles_fedora_workstation.git
config remote set-url --add origin git@github.com:Majramos/dotfiles_fedora_workstation.git
```

## Packages to install

```bash
$ sudo dnf install \
    git \
    gnome-tweaks \
    htop \
    libgtop2-devel \
    lm_sensors \
    # bootup sequence theme
    plymouth-theme-spinfinity \
    podman-compose \
    timeshift \
    vim-enhanced

curl -f https://zed.dev/install.sh | sh

$ sudo flatpak install flathub com.mattjakeman.ExtensionManager
```

### install gnome extensions with extension manager
- AppIndicator and KStatusNotifierItem Support
- Search Light
- Tiling Assistant
- Vitals

## Configure Gnome
Set Wallpaper
```bash
gsettings set org.gnome.desktop.background picture-uri file://$HOME/Pictures/oram_blue_moon.jpg
gsettings set org.gnome.desktop.background picture-uri-dark file://$HOME/Pictures/oram_blue_moon.jpg
```
set dark mode
```bash
gsettings set org.gnome.desktop.interface color-scheme prefer-dark
```
set to sort directories first in file manager (Nautilus)
```bash
gsettings set org.gtk.gtk4.Settings.FileChooser sort-directories-first true
```
set up boot up graphical theme
```bash
plymouth-set-default-theme spinfinity -R
```
