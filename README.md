# Saftopi

- Components:
    - Raspberry Pi 3 Model B
    - SanDisk Ultra Android 32 GB microSDHC Memory Card
    - Aukru® Micro USB 5 V 3 A Power Supply Charger for Raspberry Pi Model B and 3 Pi Model B/B
    - HDMI cable + micro USB cable
    - Raspberry Pi Ibetter Case For Raspberry Pi Model B + heatsinks 
    - PLAYSTATION 3 Eye
        
- Finding the pi:
```{bash}
arp -na | grep -i b8:27:eb
```
- .bashrc:

```{bash}
volume () {
    case $1 in
        ''|*[!0-9]*) echo "A valid number between 0 - 100 should be specified" ;;
        *)  local VOL=$(echo $1 | sed 's/^0*//')
            if [ $1 -gt 100 ]; then VOL=100; fi
            if [ $1 -lt 0   ]; then VOL=0;   fi
            amixer sset PCM,0 $VOL%
            echo "Volume: "$VOL"%"
            ;;
    esac
}

alias shutdownnow='sudo shutdown -h now'
```

- Mopidy Music server:
  - https://docs.mopidy.com/en/latest/installation/debian/#debian-install

- TTS:
```{bash}
#!/bin/bash
say() { local IFS=+;/usr/bin/mplayer -ao alsa -really-quiet -noconsolecontrols "http://translate.google.com/translate_tts?ie=UTF-8&client=tw-ob&q=$*&tl=en"; }
say $*

chmod u+x <filename>.sh
```
    - TODO: save the audio file, hash the sentence, check for hash before sending request

- STT: 
