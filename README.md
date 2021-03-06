## i3 tiling window manager

My primary driver is a desktop running _i3_ on [Arch Linux](https://github.com/OpcodePete/Arch-Linux).

Having used Microsoft Windows, Gnome, and KDE Plasma for years, and even macOS for a short time (a year or two), _i3_ has been the only desktop that does not get in the way. And when I learn't i3, well... it just clicked!

My _i3_ setup uses a Nordic theme, with a clean and minimalistic look and feel.

The applications I use were chosen primarily from the _Gnome_ and _KDE_ desktop environments. My development machines have sufficent RAM (PC-16GB | laptop-32GB) therefore I do not feel the need to go 'light'. I have chosen in my opinion the best apps that get the job done - don't judge bro ;)
<br />
<br />

## About
This repo was created as a backup for my installation guide and configuration files. By sharing this I hope to give back to the i3 community - helping others with their setups and configurations.
<br />
<br />

## Screenshots
![primary monitor](/screenshots/primary-monitor.png)
**Blank** - a blank workspace with i3bar
<br />
<br />
![primary monitor with rofi](/screenshots/primary-monitor-rofi.png)
**Rofi** - themed Rofi to match the desktop
<br />
<br />
![primary monitor with htop](/screenshots/primary-monitor-terminal-htop.png)
**htop** - task manager in action
<br />
<br />
![primary monitor with power menu](/screenshots/primary-monitor-powermenu.png)
**Power Menu** - power menu using rofi

<br />

To view more, please go to the /[screenshots](/screenshots) folder.

<br />

## i3 components

- Window Manager - i3-gaps
- Bar - i3status
- Launcher - rofi
- Background - feh
- Lockscreen - i3lock, xss-lock
- Notification - dunst
- Compositor - picom
<br />

## Applications
Some of the applications I use:

| Program | Name |
| ------- | ---- |
| Terminal | konsole, tmux |
| File manager | ranger, pcmanfm |
| Editor | vim, leafpad |
| Browser | firefox, chrome, edge |
| Email | Evolution |
| Office | Libre Office |
| Media | eog, vlc, deadbeed, digikam |
| AUR Helper | paru |
<br />

## Usage

**Typical workflow**

I have three monitors where specific i3 workspaces are assigned to particular monitors.

My primary monitor (which has the highest resolution) is used mostly for browsing and emails, i.e. reading. The first three _i3 workspaces_ (1-3) are assigned to this monitor.

My secondary monitor which is located in the middle is used for the builk of my work, terminal, file managers, coding, writing, and so on. Four _i3 workspaces_ (4-7) are assigned to this monitor.

My tertiary monitor which is the right most monitor has the smallest display and is by far the oldest of all my monitors. I only glance at this monitor so ad-hoc tasks are well suited here, e.g. chatting with friends via messaging apps. The last three _i3 workspaces_ (8-10) are assigned to this monitor.

The Workspace back and forth feature (workspace_auto_back_and_forth yes) is enabled.

<br />

**Automation @ start up**

Previously I had been frequently launching my most used applications (via rofi) in their designated workspaces once i3 had started. After a while I then grew tired of doing this monotonous task each time. So I looked into how this could be <u>automated<u/>. This is where _i3 Layouts_ came in!
  
I use _i3 Layouts_ to set placeholder windows for my most frequently used applications. Now when _i3_ starts, my applications auto-launch into their designated workspaces, and since workspaces appear at their specified monitors, everything is where is should be without any manual intervention!
<br />
<br />
  
Here is a snapshot on my _i3 workspaces_ and applications...


**Primary monitor (2560x1440)**
| Workspace | Application | Notes |
| ------- | ---- | ---- |
| 1 | Firefox | auto-launch at startup |
| 2 | Chrome | auto-launch at startup |
| 3 | Evolution | auto-launch at startup |
<br />

**Secondary monitor (1920x1080)**
| Workspace | Application | Notes |
| ------- | ---- | ---- |
| 4 | Konsole + tmux | auto-launch at startup |
| 5 | Ranger | auto-launch at startup |
| 6 | vim | |
| 7 | Typora | |
<br />

**Tertiary monitor (1920x1080)**
| Workspace | Application | Notes |
| ------- | ---- | ---- |
| 8 | Signal, Telegram | |
| 9 | | |
| 10 | | |

<br />

## Keybindings
Default keybindings are used wherever possible.

Mod4 (Win key) is used for mod$, which is the most popular alternative.

<br />

## Scratchpad
The _i3 scratchpad_ is very useful as I almost always have leafpad embedded here, using it solely for pasting and re-copying text.

<br />

## Starting i3
I do not use a display manager, rather I log in directly to the default shell and manually start X when I am ready. I typically carry out maintenance and ancillary tasks in the shell, e.g. _Arch Linux_ updates. No need to start X for such tasks!

To start _i3_ from the shell, X (the Xorg display server) needs to know about i3, therefore configuring _xinit_:

```bash
vim ~/.xinitrc

exec /usr/bin/i3  
```
<br />

Start _i3_:

```bash
startx

# X will look in `~/.xinitrc` and launch i3
```
<br />

If you have multipe de/wm installed, you can specifiy which to start:

```bash
# start KDE Plasma
startx startplasma-x11
  
# start i3
startx /usr/bin/i3  

# not sure if the gnome-keyring-daemon specified in .xinitrc will start
```
<br />
