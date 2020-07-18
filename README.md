# Things to do after installing Ubuntu 20.04

## Rationale

This document contains instructions I follow to configure my 2015 Macbook Pro after installing Ubuntu 20.04 Focal Fossa. While I like the default install, it doesn't quite have everything I want to have a comfortable environment. See screenshots directory to get a taste of the end result.

## Instructions

1. In settings, disable automatic display brightness adjustment

1. Install pending automatic updates and reboot

1. Configure keyboard shortcuts

1. Install gnome tweaks

    ```sh
    sudo apt-get install gnome-tweaks
    ```

1. Copy wallpapers from backup and change wallpaper using gnome-tweaks

    ```sh
    sudo cp /media/max/writable/backup/Wallpapers/* /usr/share/backgrounds
    ```
    
1. Configure extensions in Firefox

1. Install and configure Google Chrome

    ```sh
    sudo apt-get install gdebi
    cd ~/Downloads
    wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
    sudo gdebi google-chrome-stable_current_amd64.deb
    ```

    Configure extensions in Chrome

1. Install and configure the following gnome shell extensions from https://extensions.gnome.org:

    * [Coverflow Alt Tab](https://extensions.gnome.org/extension/97/coverflow-alt-tab/)
    * [Dash-to-dock](https://extensions.gnome.org/extension/307/dash-to-dock/)
    * [Disable workspace switcher popup](https://extensions.gnome.org/extension/959/disable-workspace-switcher-popup/)
    * [Gnome shell screenshot](https://extensions.gnome.org/extension/1112/screenshot-tool/)
    * [Goodbye gdm flick](https://extensions.gnome.org/extension/3037/good-bye-gdm-flick/)
    * [Gtk title bar](https://extensions.gnome.org/extension/1732/gtk-title-bar/)
    * [Panel-indicators](https://extensions.gnome.org/extension/3022/panel-indicators/)
    * [Todo.txt](https://extensions.gnome.org/extension/570/todotxt/)
    * [User themes](https://extensions.gnome.org/extension/19/user-themes/)
    * [CPU power](https://extensions.gnome.org/extension/945/cpu-power-manager/)
    * [Icon hider](https://github.com/ikalnitsky/gnome-shell-extension-icon-hider)
    * [Control blur on lock screen](https://extensions.gnome.org/extension/2935/control-blur-effect-on-lock-screen/)
    
1. Reboot

1. Install language packs and keyboards in settings

1. Unpack and apply UI theme

    ```sh
    mkdir ~/.themes
    cd ~/.themes
    tar xvf /media/max/writable/backup/Themes/Qogir-dark.tar.xz
    ```

    Use gnome-tweaks to set Shell and GTK themes

1. Unpack and apply icon theme

    ```sh
    mkdir ~/.icons
    cd ~/.icons
    tar xvf /media/max/writable/backup/Themes/Zafiro-Icons-Blue.tar.xz
    ```

    Use gnome-tweaks to set Icon theme

1. Configure login screen wallpaper

    ```sh
    sudo apt install git libglib2.0-dev
    mkdir ~/Scripts
    cd ~/Scripts
    git clone https://github.com/PRATAP-KUMAR/focalgdm3.git
    cd focalgdm3
    sudo ./focalgdm3 --set
    ```

    Follow the script's instructions to setup the wallpaper

1. Install Fira Code powerline font and configure Gnome terminal for it

    ```sh
    sudo apt install fonts-firacode
    ```

1. Install `fish` shell

    ```sh
    sudo apt-get install fish
    chsh -s /usr/bin/fish
    ```
    
    Reboot
    
    ```sh
    sudo apt install curl
    curl -L https://get.oh-my.fish | fish
    omf install agnoster
    echo "set fish_greeting" > ~/.config/fish/config.fish
    ```    

1. Install text editors

    ```sh
    sudo apt install micro vim
    ```
    
1. Install Noto fonts and configure the UI fonts in settings

    ```sh
    sudo apt install fonts-noto-core fonts-noto-extra
    ```

1. Disable annoyances

    ```sh
    cd /usr/share/dbus-1/services
    sudo mv org.gnome.Shell.Notifications.service org.gnome.Shell.Notifications.service.disabled
    sudo apt install dconf-editor
    ```

    In dconf editor, set `org.gnome.desktop.sound` to `False`


1. Update to the latest version of packages

    ```sh
    sudo apt-get update
    sudo apt-get upgrade
    ```
    
1. Remove unneeded packages

    ```sh
    sudo apt autoremove
    ```
        
    Reboot for a good measure

1. Disable bluetooth

1. Install nim

    ```sh
    curl https://nim-lang.org/choosenim/init.sh -sSf | sh
    echo "set -gx PATH /home/max/.nimble/bin \$PATH" >> ~/.config/fish/config.fish
    ```
    
    Restart terminal and test
    ```sh
    nim --version
    ```

1. Remove default Gnome shell extensions to prevent conflicts with the ones we installed earlier

    ```sh
    sudo rm -Rf /usr/share/gnome-shell/extensions/*
    ```

1. Install Nim file renamer `fren`

    Follow instructions https://github.com/rustomax/nim-fren/blob/master/README.md
    
1. Install useful gEdit plugins, including Nim syntax highlighter and MD preview

    ```sh
    sudo apt-get install gedit-plugins
    cd /usr/share/gtksourceview-4/language-specs
    sudo wget https://raw.githubusercontent.com/nim-lang/Aporia/master/share/gtksourceview-2.0/language-specs/nim.lang
    sudo apt install python3-markdown pandoc gir1.2-webkit2-4.0 git
    git clone https://github.com/maoschanz/gedit-plugin-markdown_preview
    cd gedit-plugin-markdown_preview/
    ./install.sh
    ```

    Restart gEdit and enable desired plugins
    
1. Install additional software
    * Lollypop music player
    * Shotwell photo manager
    * Celluloid video player

## Legalese

* Obviously, what I want in my system might be quite different from what someone else might need. If following these instructions blows up your PC, that's your responsiblity.

* Screenshots and sources in this repo might contain copyrighted material. They are included for illustration purposes only and not intended to infringe in any way. However, if you are the copyright holder and don't want your content here, let me know and I'll take it down.

