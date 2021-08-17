# i3 Installation guide

## Configure multiple monitors

For _Nvidia graphics card_ owners, use the Nvidia tool to configure for multi-monitor
```bash
sudo pacman -S nvidia-settings
```
<br />

For other graphics card types
```bash
# install
sudo pacman -S xorg-xrandr arandr

# get monitors details
xrandr

# generate multi-monitor configuration
arandr

# place the generated configuration in the i3 config file appropriately
```
<br />

## Install i3

```bash
sudo pacman -S i3 rofi dunst picom feh xss-lock polkit perl-anyevent-i3 perl-json-xs
# note the i3 package group contains both i3 and i3-gaps, choose one of them
```
<br />

## Install applications

```bash
# aur helper
cd AUR
git clone https://aur.archlinux.org/paru.git
cd paru
makepkg -si

# terminal and related utilities
sudo pacman -S konsole bash-completion tmux
paru tmuxline

# file managers
sudo pacman -S pcmanfm ranger

# editors
sudo pacman -S vim leafpad

# browsers
sudo pacman -S firefox chromium

# email client
sudo pacman -S evolution evolution-ews evolution-on evolution-rss

# office suite and related applications
sudo pacman -S libreoffice-still freerdp foliate evince kcalc flameshot akregator hunspell-en_AU hyphen-en libmythes mythes-en aspell-en
paru typora
paru cawbird
paru zoom
paru teams

# media applications
sudo pacman -S eog vlc deadbeef digikam

# archive tools
sudo pacman -S p7zip unrar tar ark

# Security tools
sudo pacman -S gnome-keyring veracrypt
paru cryptomator

# system utilities
sudo pacman -S man-db man-pages arch-audit rsync redshift

# diagnostics tools
sudo pacman -S htop ncdu filelight gnome-disk-utility gparted neofetch
paru pkgbrowser

# development tools
sudo pacman -S nasm kdbg bless code
```
<br />

## Set system theme

```bash
# install theme utilities
sudo pacman -S arc-gtk-theme arc-icon-theme lxappearance qt5ct oxygen oxygen-icons gtk-chtheme

# install fonts
sudo pacman -S ttf-roboto ttf-roboto-mono ttf-nerd-fonts-symbols

# Set theme to 'Breeze'
lxappearance

# Set theme to 'Breeze'
qt5ct --platformtheme qt5ct

# Set theme to 'Breeze'
gtk-chtheme
```
<br />

## Set Konsole theme

Under Menu/Settings/General

1. Show menubar - Uncheck and restart Konsole

Under Menu/Settings/Profiles/Profile 1/Edit

1. Set Font to `Roboto Mono [GOOG] Light 8pt`

2. Set Appearance to `Nordic konsole` (Download by clicking [Get New...] button)

<br />

## Configure bash

```bash
# vim ~/.bashrc
# set the default editor

export VISUAL=vim
export EDITOR="$VISUAL"
```
<br />

## Configure tmux

```bash
# vim ~/.tmux.conf
# configure tmux to support 256 colours

set -g default-terminal "xterm-256color"
set -ag terminal-overrides ',xterm-256color:Tc'
```
<br />

## Configure vim under tmux

```bash
# vim ~/.vimrc

"Use 24-bit (true-color) mode in Vim/Neovim when outside tmux.
if (has("termguicolors"))
   set termguicolors
endif

if &term =~ '256color'
    " disable Background Color Erase (BCE) so that color schemes
    " render properly when inside 256-color tmux and GNU screen.
    " see also http://snk.tuxfamily.org/log/vim-256color-bce.html
    set t_ut=
endif
set term=xterm-256color
```
<br />

## Configure pacman

```bash
# enable colour
sudo vim /etc/pacman.conf

# in the 'Misc options' section, unremark option 'Color'
```
<br />

## Configure paru

```bash
sudo vim /etc/paru.conf

# in the 'General option' section, unremark 'ColorBottomUp'
```
<br />

## Configure Ranger

```bash
# configure columns
vim ~/.config/ranger/rc.conf#set column_ratios 1,3,4set column_ratios 2,4
```
<br />

## Configure Firefox

Install the Firefox Addon _Arc Darker Theme_

<br />

## Configure Gnome Keyring

```bash
sudo vim /etc/pam.d/login

# At the end of the 'auth' section add the following:
auth     optional    pam_gnome_keyring.so

# At the end of the 'session' section add the following:
session     optional    pam_gnome_keyring.so auto_start
```
<br />

## Configure Redshift

```bash
# Verify geoclue is working
/usr/lib/geoclue-2.0/demos/where-am-i

# Edit the geoclue config
sudo vim /etc/geoclue/geoclue.conf

# Uncomment the following line to:
url=https://location.services.mozilla.com/v1/geolocate?key=geoclue

# Add the following lines to the end of the file:
[redshift]
allowed=true
system=false
users=
```
<br />

## Configure Evolution

```bash
vim ~/.xinitrc

eval $(gnome-keyring-daemon --start)
export SSH_AUTH_SOCK
```
Note when adding an Office365 mail account, select the _Server Type_ as _Exchange Web Services_

<br />
<br />

## i3 Layout saving and restoring

Saving the layouts

```bash
# go to my layouts folder
cd /home/peterg/.config/i3/layouts

# workspace 1 launch Firefox

# save the layout
i3-save-tree --workspace 1 > build_workspace.json

# format the layout and clean up
tail -n +2 build_workspace.json | fgrep -v '// split' | sed 's|//||g' > workspace_1_startup.json
rm build_workspace.json


# workspace 2 launch Chrome

# save the layout
i3-save-tree --workspace 2 > build_workspace.json

# format the layout and clean up
tail -n +2 build_workspace.json | fgrep -v '// split' | sed 's|//||g' > workspace_2_startup.json
rm build_workspace.json


# workspace 3 launch Evolution

# save the layout
i3-save-tree --workspace 3 > build_workspace.json

# format the layout and clean up
tail -n +2 build_workspace.json | fgrep -v '// split' | sed 's|//||g' > workspace_3_startup.json
rm build_workspace.json


# workspace 4 launch Konsole + tmux

# save the layout
i3-save-tree --workspace 4 > build_workspace.json

# format the layout and clean up
tail -n +2 build_workspace.json | fgrep -v '// split' | sed 's|//||g' > workspace_4_startup.json
rm build_workspace.json


# workspace 5 launch Konsole + ranger

# save the layout
i3-save-tree --workspace 5 > build_workspace.json

# format the layout and clean up
tail -n +2 build_workspace.json | fgrep -v '// split' | sed 's|//||g' > workspace_5_startup.json
rm build_workspace.json
```
<br />

Restoring the layouts

```bash
# create a script fo restore layout
vim load_startup_layouts.sh

#!/bin/bash

# For each workspace, append saved layouts then fill containers with specified programs
# Note: call workspaces in ascending order of application load times
i3-msg "workspace 4; append_layout ${XDG_CONFIG_HOME}/i3/layouts/workspace_4_startup.json"
sleep 1
(konsole -e tmux &)
sleep 1

i3-msg "workspace 5; append_layout ${XDG_CONFIG_HOME}/i3/layouts/workspace_5_startup.json"
(konsole -e ranger &)
sleep 1

i3-msg "workspace 1; append_layout ${XDG_CONFIG_HOME}/i3/layouts/workspace_1_startup.json"
(firefox &)

i3-msg "workspace 2; append_layout ${XDG_CONFIG_HOME}/i3/layouts/workspace_2_startup.json"
(google-chrome-stable &)

i3-msg "workspace 3; append_layout ${XDG_CONFIG_HOME}/i3/layouts/workspace_3_startup.json"
(evolution &)
```

<br />

To manually configure swallows in window layouts use `xprop`

```bash
# Get the properties of the application
xprop
# The click in the app with the crosshairs (mouse cursor)

# Layout swallow matching
# Match on "class", "instance", "window_role" and/or "title" (all values are case-sensitive regular expressions):
WM_WINDOW_ROLE(STRING) = "gimp-toolbox-color-dialog"

# The first part of WM_CLASS is the "instance" (gimp-2.8 in this case), the second part is the "class" (Gimp-2.8 in this case)
WM_CLASS(STRING) = "gimp-2.8", "Gimp-2.8"

#  "title" matches against _NET_WM_NAME 
_NET_WM_NAME(UTF8_STRING) = "Change Foreground Color"

# "window_role" matches against WM_WINDOW_ROLE

# Or if you quickly just want the class name of an application
xprop | grep -i 'class'
```
