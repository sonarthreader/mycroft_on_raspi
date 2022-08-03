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

## ReSpeaker 2-Mics Pi HAT

Source: https://github.com/respeaker/seeed-voicecard#readme

```
# sudo apt-get install git
# git clone https://github.com/respeaker/seeed-voicecard
# cd seeed-voicecard
# sudo ./install.sh --compat-kernel
# sudo reboot
```

Check if it works
```
mycroft@raspberrypi:~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: seeed2micvoicec [seeed-2mic-voicecard], device 0: bcm2835-i2s-wm8960-hifi wm8960-hifi-0 [bcm2835-i2s-wm8960-hifi wm8960-hifi-0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
mycroft@raspberrypi:~ $ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: seeed2micvoicec [seeed-2mic-voicecard], device 0: bcm2835-i2s-wm8960-hifi wm8960-hifi-0 [bcm2835-i2s-wm8960-hifi wm8960-hifi-0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
Just seeed devices, no onboard audio

## Install pulseaudio
```
# sudo apt-get install pulseaudio
# sudo shutdown -r now

```
