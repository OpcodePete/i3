# i3 tiling wm
<br />

## My i3
My primary driver is a desktop with _i3_ and _Arch Linux_.

Having used Microsoft Windows, Gnome, and KDE Plasma for years, and even macOS for a short time (a year or two), i3 has been the only desktop that does not get in the way. And when I learn't i3, well... it just clicked!

My _i3_ setup uses a Nordic theme, with a clean and minimalistic look and feel.

The applications I use were chosen primarily from the _Gnome_ and _KDE_ desktop environments. My development machines have sufficent RAM (PC-16GB|laptop-32GB) therefore I do not feel the need to go 'light'. I have chosen in my opinion the 'best' apps that can get the job done - don't judge bro ;)
<br />
<br />

## About
This repo was created as a backup for my installation guide and configuration files. By sharing this I hope to give back to the i3 community - helping others with their setups and configurations.
<br />
<br />

## Screenshots
A blank workspace
![primary monitor](/screenshots/primary-monitor.png)
<br />
<br />
Rofi in action
![primary monitor with rofi](/screenshots/primary-monitor-rofi.png)
<br />
<br />
htop in action
![primary monitor with htop](/screenshots/primary-monitor-terminal-htop.png)
<br />
<br />
To view more, please go to the /[screenshots](/screenshots) folder.
<br />
<br />

## Components
The main i3 components I have used:

- WM - i3-gaps
- Launcher - rofi
- Bar - i3status
- Background - feh
- Screen lock - xss-lock
- Notification - dunst
- Compositor - picom
<br />

## Applications
The main applications I regularly use.

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

**My typical workflow**

I have three monitors and have specific i3 workspaces assigned to each of the monitors.

My primary monitor (which has the highest resolution) is used mostly for browsing and emails, i.e. reading. The first three _i3 workspaces_ (1-3) are assigned to this monitor.

My secondary monitor which is located in the middle is used for the builk of my work, terminal, file managers, coding, writing, and so on. Four _i3 workspaces_ (4-7) are assigned to this monitor.

My tertiary monitor which is the right most monitor has the smallest display and is by far the oldest of all my monitors. I only glance at this monitor so ad-hoc tasks are well suited here, e.g. chatting with friends via messaging apps, using a gui-based editor to paste temporary text (although I could use the _i3 scratchpad_ for this purpose), and so on.  The last three _i3 workspaces_ (8-10) are assigned to this monitor.
<br />
<br />

**Automation @ start up**

Previously I had been frequently launching my most used applications (via rofi) in their designated workspaces once i3 had started. After a while I then grew tired of doing this monotonous task each time. So I looked into how this could be <u>automated<u/>. This is where _i3 Layouts_ came in!
  
I use _i3 Layouts_ to set placeholder windows for my most frequently used applications. Now when _i3_ starts, my applications auto-launch into their designated workspaces, and since workspaces appear at their specified monitors, everything is where is should be without any manual intervention!
<br />
<br />
  
Here is a snapshot on my _i3 workspaces_ and applications...

<br />

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
| 6 | PCManFM | |
| 7 | Typora | |
<br />

**Tertiary monitor (1920x1080)**
| Workspace | Application | Notes |
| ------- | ---- | ---- |
| 8 | Signal, Telegram | |
| 9 | | |
| 10 | | |

<br />
<br />

## Display Manager
I don't use a display manager (aka login manager), rather I prefer to log into the default shell and manually start _X_ typically after _Arch Linux_ updates.

<br />
<br />

## Keybindings
I stick to all the default keybindings where possible and for mod$ I use the popular alternative Windows key (Mod4).

I have enabled back and forth (workspace_auto_back_and_forth yes)
