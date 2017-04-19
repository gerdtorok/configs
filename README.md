# configs

## x240 manjaro i3
### sound
install `pulseaudio` and `pavucontrol`

* in Volume Icon settings select Device `default` & Channel `master`
* in pavucontrol select Configuration Profile `Analog Stereo Duplex`

### touchpad
`/etc/X11/xorg.conf.d/40-touchpad.conf`
```
# Touchpad with libinput
#
Section "InputClass"
        Identifier "touchpad catchall"
        Driver "libinput"
        MatchIsTouchpad "on"

        # features
        Option  "Tapping"               "on"
        Option  "TappingButtonMap"      "lrm" # 1/2/3 finger taps correspond to which button; left/right/middle
        Option  "NaturalScrolling"      "True"
        Option  "DisableWhileTyping"    "on"
EndSection
```
### keyboard
remove all other keyboard elements from xorg.conf.d files (99-..), allows to switch layout with simulteanous CTRLs press
`/etc/X11/xorg.conf.d/00-keyboard.conf`
```
# Read and parsed by systemd-localed. It's probably wise not to edit this file
# manually too freely.
Section "InputClass"
        Identifier "system-keyboard"
        MatchIsKeyboard "on"
        Option "XkbLayout" "de,us"
        Option "XkbModel" "pc105"
        Option "XkbVariant" "nodeadkeys,altgr-intl"
        Option "XkbOptions" "grp:ctrls_toggle,terminate:ctrl_alt_bksp"
EndSection
```
