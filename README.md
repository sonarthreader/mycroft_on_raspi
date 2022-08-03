# Mycroft on Raspberry Pi
As official Picroft images seems stale I do my own installation on Raspberry Pi OS Lite on Raspberry 3B with ReSpeaker 2-Mics Pi HAT

## Install Raspberry Pi OS Lite
Read https://www.raspberrypi.com/documentation/computers/getting-started.html and stick to the manual :)

After installation don't forget to
- change password
- set hostname
- configure WiFi
- enable SPI
- enable SSH

Using the audio from ReSpeaker HAT you have so disable onboard audio
```
# /boot/config.txt
dtparam=audio=off
hdmi_ignore_edid_audio=1
dtoverlay=i2s-mmap
dtparam=i2s=on

# as root
echo "blacklist snd_bcm2835" > /etc/modprobe.d/blacklist-bcm2835.conf
```

