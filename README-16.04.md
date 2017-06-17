# ubuntu-gnome-windowmaker
Setting up Gnome panel + WindowMaker on Ubuntu

## Install packages 

Install up-to-date version of [WindowMaker](https://launchpad.net/~profzoom/+archive/ubuntu/wmaker).


```
sudo add-apt-repository ppa:profzoom/wmaker
sudo apt update
sudo apt install --yes wmaker
sudo apt install --yes gnome-session-flashback
```


## Install package

* Copy files from this repository under corresponding paths in your system.
* Logout 
* Select 'Gnome Flashback Session (Wmaker)' in your session seelction menu
* Login


## Disable Desktop Menu

By default Nautilus manages desktop and right click on empty screen space may
show up Gnome menu and not WindowMaker's application menu.

### Graphical interface

```
sudo apt install --yes gnome-tweak-tool
gnome-tweak-tool
```

Navigate to 'Desktop' and turn off 'Icons on Desktop' switch.

### Command line

Disable with: 
```
gsettings set org.gnome.desktop.background show-desktop-icons false
```

Re-enable with
```
gsettings set org.gnome.desktop.background show-desktop-icons true
```


## Manage Gnome Panel

Gnome Panel is configured by Alt-right click on it. But by default WindowMaker
grabs event to Gnome Panel and does not let you right click and configure it.

To manage Gnome Panel open `~/GNUstep/Defaults/WMWindowAttributes` and add/modify section `gnome-panel.Gnome-panel`

```
  "gnome-panel.Gnome-panel" = {
    NoMouseBindings = Yes;
    NoKeyBindings = Yes;
    SkipWindowList = Yes;
    NoTitlebar = Yes;
    SkipSwitchPanel = Yes;
    KeepInsideScreen = Yes;
    NoMiniaturizable = Yes;
    NoMiniaturizeButton = Yes;
    NoBorder = Yes;
    AlwaysUserIcon = No;
    NoResizebar = Yes;
    NoCloseButton = Yes;
    Omnipresent = Yes;
  };
```

You need to add these two lines, save file and then choose from WindowMaker menu 'Restart WindowMaker'.
If such section does not exists - add it and do not forget `;` as entries separator.

```
    NoMouseBindings = Yes;
    NoKeyBindings = Yes;
```

After restart or logout/login you should be able to Alt+right-click on Gnome Panel and add/modiry indicators.





