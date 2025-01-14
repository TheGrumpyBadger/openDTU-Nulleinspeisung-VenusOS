# openDTU-Nulleinspeisung-VenusOS

Um das Script auf VenusOS (Raspberry Pi oder Victron Cerberus) zu starten müssen die Script und Abhängigkeiten angepasst werden.
Als Grundlage dient das Script von Kotty666 ( https://github.com/Kotty666/openDTU-NullEinSpeisung ).


Durch die Inspiration von https://selbstbau-pv.de/wissensbasis/nulleinspeisung-hoymiles-hm-1500-mit-opendtu-python-steuerung/ entstand dieses Script
Es Dient dazu da einen oder mehrere Shelly-3EM auszulesen und deren Stromverbrauch in Einklang mit der Solar-Produktion zu bekommen.
Die Produktionsdaten kann von einer oder mehreren openDTUs kommen.

## Installation vorbereiten

Das Script benötigt Python3, pip3  und dort muss noch das modul pyyaml nachinstalliert werden.


```
opkg update
opkg install python3-pip
pip3 install pyyaml
```

# Install & Configuration
## Get the code
```
wget https://github.com/TheGrumpyBadger/openDTU-Nulleinspeisung-VenusOS/archive/refs/heads/main.zip
unzip main.zip
rm main.zip
mv openDTU-Nulleinspeisung-VenusOS-main/ openDTU-Nulleinspeisung/
cd /data/openDTU-Nulleinspeisung/
nano config.yaml
sh ./install.sh
```

## Configuration
Die Komplette Konfiguration befindet sich in der datei config.yaml
### Parameters
logInterval - Alle wie viel Minuten das Script in einen Status in sein logfile (current.log) schreiben will - default 1 Minute 
openDTU - Hiernach folgt der Block für die OpenDTUs - NICHT VERÄNDERN
dev - der Interne Name einer DTU, für jede DTU ein eigener Name
ip - die IP der OpenDTU kann auch ein Hostname sein - muss allerdings vom DNS Auflösbar sein
user - user für die openDTU
password - dazugehöriges Passwort
3EM - Überschrift für die 3EM - NICHT VERÄNDERN
eg - Interner Name des 3EM
ip - die IP des 3EM
user - falls der 3EM mit user / passwort geschützt ist kommt hier der User rein, wenn nicht entsprechend so lassen
password - falls der 3EM mit user / passwort geschützt ist kommt hier das Passowrt rein, wenn nicht entsprechend so lassen

### Beispiel Konfig mit mehreren DTUs und mehreren 3EM:
```
---
logInterval: 1
openDTU:
  garage:
    ip: 192.168.178.201
    user: admin
    password: openDTU42
  hausdach:
    ip: 192.168.178.202
    user: elefant
    password: ruessel
3EM:
  eg:
    ip: 192.168.178.236
    user: ''
    password: ''
  og:
    ip: 192.168.178.237
    user: ''
    password: ''
```

