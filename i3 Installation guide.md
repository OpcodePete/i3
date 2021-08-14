# i3 Installation guide

## Pre-requisites

**Monitor(s) configuration**

<u>Nvidia graphics card</u>

```bash
sudo pacman -S nvidia-settings
```

Then configure monitors appropriately

​			OR

<u>Other graphics card</u>

```bash
sudo pacman -S xorg-xrandr
```

Generate configuration

```bash
# List monitors
xrandr --listmonitors
# or
xrandr
```





## Installation

Notes:

1. Configuration files reside in the below directories
2. My 'live' config files are in: `OneDrive/Computing/Linux/Notes/Windows Managers/i3wm/Live/Desktop/`

```bash
#~/
~/.Xresources

#i3
~/.config/i3/config
~/.config/i3/nord-wallpaper.png

#i3status
~/.config/i3status/config

#rofi
~/.config/rofi/config
~/.config/rofi/nord.rasi
~/.config/rofi/rofi-power-menu

#dunst
~/.config/dunst/dunstrc

#picom
~/.config/picom/picom.conf
```



**i3**

Note, monitor names will be used in the i3 configurations.

i3  and related apps

```bash
sudo pacman -S i3 rofi dunst picom feh xss-lock polkit perl-anyevent-i3 perl-json-xs
```



**Themes**

Themes and appearance related apps

```bash
sudo pacman -S arc-gtk-theme arc-icon-theme lxappearance qt5ct oxygen oxygen-icons gtk-chtheme
```

Fonts

```bash
sudo pacman -S ttf-roboto ttf-roboto-mono ttf-nerd-fonts-symbols
```

Set theme

```bash
# Set theme to 'Breeze'
lxappearance

# Set theme to 'Breeze'
qt5ct --platformtheme qt5ct

# Set theme to 'Breeze'
gtk-chtheme
```



**Applications**

Install applications

Terminal

```bash
sudo pacman -S konsole bash-completion tmuxparu tmuxline
```

File Manager

```bash
sudo pacman -S pcmanfm nnn
```

Editor

```bash
sudo pacman -S vim leafpad
```

Browser

```bash
sudo pacman -S firefox chromium
```

Email

```bash
sudo pacman -S evolution evolution-ews evolution-on evolution-rss
```

Office

```bash
sudo pacman -S libreoffice-still freerdp foliate evince kcalc flameshot akregator hunspell-en_AU hyphen-en libmythes mythes-en aspell-enparu typoraparu cawbirdparu zoomparu teams
```

Media

```bash
sudo pacman -S eog vlc deadbeef digikam
```

Archive Tools

```bash
sudo pacman -S p7zip unrar tar ark
```

Security

```bash
sudo pacman -S gnome-keyring veracryptparu cryptomator
```

Utilities

```bash
sudo pacman -S man-db man-pages arch-audit rsync redshift
```

Diagnostics

```bash
sudo pacman -S htop ncdu filelight gnome-disk-utility neofetchparu pkgbrowser
```

System

```bash
sudo pacman -S gparted
```

Development

```bash
sudo pacman -S nasm kdbg bless code
```

Games

```bash
sudo pacman -S gnuchess knights
```

AUR Helper

```bash
cd AURgit clone https://aur.archlinux.org/paru.gitcd parumakepkg -si
```

Review apps: https://discover.manjaro.org/





## Configuration

**System**

<u>bash</u>

Include the following in ~/.bashrc

```bash
# Set default editorexport VISUAL=vimexport EDITOR="$VISUAL"
```



<u>tmux</u>

Configure tmux to support 256 colours

In ~/.tmux.conf

```bash
set -g default-terminal "xterm-256color"set -ag terminal-overrides ',xterm-256color:Tc'
```

vim (in tmux)

```bash
"Use 24-bit (true-color) mode in Vim/Neovim when outside tmux.if (has("termguicolors"))  set termguicolorsendifif &term =~ '256color'    " disable Background Color Erase (BCE) so that color schemes    " render properly when inside 256-color tmux and GNU screen.    " see also http://snk.tuxfamily.org/log/vim-256color-bce.html    set t_ut=endifset term=xterm-256color                                                                                                             "If the above does not work, use the below snippet instead"if exists('+termguicolors')                                                                                              "  let &t_8f = "\<Esc>[38;2;%lu;%lu;%lum"                                                                                 "  let &t_8b = "\<Esc>[48;2;%lu;%lu;%lum"                                                                                 "  set termguicolors                                                                                                      "endif                  
```



Notes:
If tmux does not render the **vim-airline** powerline fonts correctly, e.g. sharp arrow corners are not displayed, then:

1. Check system locales

```bash
locale# Locales should display: en_AU.UTF-8
```

If locales are not set, then check the Arch installation to set locales in `/etc/locale.conf`

If still not working, then force tmux to output UTF-8:

```bash
# In ~/.bashrc, create an alias to a) force 256 colour support, and b) write UTF-8 outputalias tmux='tmux -2u'# Apply changes without rebootingsource ~/.bashrc
```



**Applications**

<u>Pacman</u>

Enable colour for pacman

```bash
cd /etcsudo vim pacman.conf# Unremark the Misco option: ColorColor
```

<u>Paru</u>

```bash
cd /etcsudo vim paru.conf# Unremark the General option: ColorBottomUp
```

<u>Konsole</u>

​	Menu/Settings/General

1. Show menubar - Uncheck and restart Konsole

​	Menu/Settings/Profiles/Profile 1/Edit

1. Set Font to `Roboto Mono [GOOG] Light 8pt`

2. Set Appearance to `Nordic konsole` (Download by clicking [Get New...] button)

<u>Ranger</u>

Configure columns

```bash
vim ~/.config/ranger/rc.conf#set column_ratios 1,3,4set column_ratios 2,4
```

<u>Firefox</u>

1. Install Firefox Addon *Arc Darker Theme*

<u>Gnome Keyring</u>

```bash
sudo vim /etc/pam.d/login# At the end of the auth section add:auth optional pam_gnome_keyring.so  # At the end of the session section add:session optional pam_gnome_keyring.so auto_start
```

<u>Redshift</u>

```bash
# Verify geoclue is working/usr/lib/geoclue-2.0/demos/where-am-i# Edit geoclue configsudo vim /etc/geoclue/geoclue.conf# Edit the following line:url=https://location.services.mozilla.com/v1/geolocate?key=geoclue# Add the following lines:[redshift]allowed=truesystem=falseusers=
```

<u>Evolution</u>

```bash
vim ~/.xinitrceval $(gnome-keyring-daemon --start)export SSH_AUTH_SOCK
```

When adding opcodestudios account, select **Server Type** as **Exchange Web Services**



**Layouts**

Launch applications

Save layouts

```bash
# Workspace 1# Launch firefoxcd /home/peterg/.config/i3/layoutsi3-save-tree --workspace 1 > build_workspace.jsontail -n +2 build_workspace.json | fgrep -v '// split' | sed 's|//||g' > workspace_1_startup.jsonrm build_workspace.json# Workspace 2# Launch konsolei3-save-tree --workspace 1 > build_workspace.jsontail -n +2 build_workspace.json | fgrep -v '// split' | sed 's|//||g' > workspace_2_startup.jsonrm build_workspace.json# Workspace 4# Launch konsole, rangeri3-save-tree --workspace 1 > build_workspace.jsontail -n +2 build_workspace.json | fgrep -v '// split' | sed 's|//||g' > workspace_4_startup.jsonrm build_workspace.json# Workspace 10# Launch thunderbirdi3-save-tree --workspace 1 > build_workspace.jsontail -n +2 build_workspace.json | fgrep -v '// split' | sed 's|//||g' > workspace_10_startup.jsonrm build_workspace.json
```

Notes:

1. How to get the class name of an application

```bash
# In a terminal, execute the followingxprop | grep -i 'class'# Then click on the target application
```



2. How to configure swallows in window layouts

```bash
# Get the properties of the applicationxprop# The click in the app with the crosshairs (mouse cursor)# Layout swallow matching# Match on "class", "instance", "window_role" and/or "title" (all values are case-sensitive regular expressions):WM_WINDOW_ROLE(STRING) = "gimp-toolbox-color-dialog"# The first part of WM_CLASS is the "instance" (gimp-2.8 in this case), the second part is the "class" (Gimp-2.8 in this case)WM_CLASS(STRING) = "gimp-2.8", "Gimp-2.8"#  "title" matches against _NET_WM_NAME _NET_WM_NAME(UTF8_STRING) = "Change Foreground Color"# "window_role" matches against WM_WINDOW_ROLE
```





## How To

**How to manually start i3**

Use `startx` with an option parameter:

```bash
startx /usr/bin/i3
```

When not specifying an optional parameter, X will look in `~/.xinitrc` and launch *KDE*

Else to start i3 automatically using `startx`, modify the config:

```bash
vim .xinitrc
exec /usr/bin/i3

# Start i3
startx
```



**How to Test dunst**

```bash
dunstify "It works"

# Clear notification
[Ctrl][space]

# Show previous notification
[Ctrl][.]
```



**How to obtain the rofi power menu script**

```bash
# Install
cd ~/AUR
git clone https://github.com/jluttine/rofi-power-menu.git
cd rofi-power-menu.git
sudo cp rofi-power-menu /home/peterg/.config/rofi/
```

