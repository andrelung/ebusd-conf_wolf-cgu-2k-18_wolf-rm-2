# ebusd-conf_wolf-cgu-2k-18_wolf-rm-2
ebusd csv files for wolf cgu-2k-18 and wolf rm-2

# Currently this is work in progress
... as I am exploring the csv format and the commands on my bus.

# My System identifies as:
```
[update notice] sent scan-read scan.08  QQ=31: ENCON;  ;-;-
[bus notice] scan 08: ;ENCON;  ;-;-
[main notice] read scan config file encon/08..hc.csv for ID "", SW65535, HW65535

[update notice] sent scan-read scan.35  QQ=31: Wolf; 8;0110;0000
[bus notice] scan 35: ;Wolf; 8;0110;0000
[main notice] read scan config file wolf/35..hc.csv for ID "8", SW0110, HW0000

[main error] scan config f6: ERR: read timeout
```
as far as I can identify this, 
- 08 seems to be the Burner (CGU-2K-18)
- 35 seems to be the Raumregler (RM-2)
... and I think there are not other components in my system (like outdoor temperature or mixer)

ebusd interprets several command types as:
- BC = Burner Circruit
- MS = ? maybe: MS = Master (the bus master / master station, usually the main controller/boiler control that coordinates communication)
- MM = ? maybe: MM = Mixer Module (German “Mischermodul”) 


# my ebusd setup:
- easi firmware Build: 20260104
- eBUS Adapter Stick C6
- connected via WiFi (ethernet is planned)
- ebusd installed as Home Assistant Addon https://github.com/LukasGrebe/ha-addons
- connection ebusd <> ha via mqtt
- i did follow this guide: https://github.com/john30/ebusd/discussions/1177

# Please be careful
I am no expert and these files are not validated in any kind of way.

# No changes have been made to:
- mqtt-hassio.cfg


# What I do not understand (yet)
Any help and explanations are appreciated :)
- what is a master?
````
[bus notice] new master 30, master count 2
[bus notice] new master 03, master count 3
[bus notice] new master f1, master count 4
```
- and why do the numbers differ (08 + 35 are my adresses, i guess)
- is maybe one of these masters the ebus adapter stick itself?
    - probably not, since: [bus notice] bus started with own address 31/36