Display Wayland 

```
sudo nano /etc/gdm3/custom.conf
WaylandEnable=false
sudo systemctl restart gdm3
```

```
sudo apt-get install xserver-xorg-video-dummy
```

Then write it in the /usr/share/X11/xorg.conf.d/xorg.conf (or possibly /etc/X11/xorg.conf) file (create one, if it does not exist):

```
Section "Device"
    Identifier  "Configured Video Device"
    Driver      "dummy"
    # Default is 4MiB, this sets it to 16MiB
    VideoRam    16384
EndSection

Section "Monitor"
    Identifier  "Configured Monitor"
    HorizSync 31.5-48.5
    VertRefresh 50-70
EndSection

Section "Screen"
    Identifier  "Default Screen"
    Monitor     "Configured Monitor"
    Device      "Configured Video Device"
    DefaultDepth 24
    SubSection "Display"
    Depth 24
    Modes "1024x800"
    EndSubSection
EndSection

```