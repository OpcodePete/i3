# i3 tiling window manager

## My i3
My primary driver is **Arch Linux** with **i3** on my desktop.

i3 is the only desktop (wm) that does not get in the way. Using other tiling window mangers was not intuitive for me, but using i3, well... it just clicked!

My **i3** setup uses a Nordic theme, with a clean and minimalistic look and feel.

The applications I use were chosen primarily from the Gnome and KDE desktop environments. My development machines have sufficent memory (PC:16GB RAM, laptop:32GB RAM) therefore I do not feel the need to go 'light'. I have chosen in my opinion the 'best' apps that can get the job done - don't judge bro ;)
<br />
<br />
## About
This repo was created as a backup for my installation guide and configuration files. By sharing this I hope to give back to the i3 community - helping others with their setups and configurations.
<br />
<br />
## Screenshots
A blank workspace
![primary monitor](https://github.com/OpcodePete/i3/blob/main/screenshots/primary-monitor.png)
<br />
<br />
Rofi in action
![primary monitor with rofi](https://github.com/OpcodePete/i3/blob/main/screenshots/primary-monitor-rofi.png)
<br />
<br />
htop in action
![primary monitor with htop](https://github.com/OpcodePete/i3/blob/main/screenshots/primary-monitor-terminal-htop.png)
<br />
<br />
To view more go to the /[screenshots](https://github.com/OpcodePete/i3/tree/main/screenshots) folder.
<br />
<br />
## Components
The main i3 components used.

| Program | Name |
| ------- | ---- |
| WM | i3-gaps |
| Launcher | rofi |
| Bar | i3status |
| Background | feh |
| Notification | dunst |
| Compositor | picom |
<br />
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
<br />

## Usage

**My typical workflow**
I have three monitors and have set specific i3 workspaces assigned to each of the monitors.

My primary monitor (which has the highest resolution) is used for mostly for browsing and emails, i.e. mostly reading. Three i3 workspaces (1-3) are assigned to this monitor.

The monitor in the middle (the secondary monitor) is used for the builk of my work, terminal, coding, writing, and so on. Four i3 workspaces (4-7) are assigned to this monitor.

The right most monitor is the (oldest and) smallest monitor. I only glance at this monitor. I find ad-hoc tasks are well suited here, such as chatting with friends via messaging apps, a GUI based editor to paste temporary text (although I could use the i3 scratchpad for this).  Three i3 workspaces (8-10) are assigned to this monitor.

**Automation @ start up**

I use _i3 Layouts_ to set placeholder windows for my most frequently used applications. When i3 starts, workspaces appear at their set monitors, and my applications auto-launch into their set workspaces!


**Primary monitor (2560x1440)**
| Workspace | Application | Notes |
| ------- | ---- | ---- |
| 1 | Firefox | |
| 2 | Chrome | |
| 3 | Evolution | |
<br />

**Secondary monitor (1920x1080)**
| Workspace | Application | Notes |
| ------- | ---- | ---- |
| 4 | Konsole + tmux | |
| 5 | Ranger | |
| 6 |  | |
| 7 |  | |
<br />

**Tertiary monitor (1920x1080)**
| Workspace | Application | Notes |
| ------- | ---- | ---- |
| 8 |  | |
| 9 |  | |
| 10 |  | |
