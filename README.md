# pi-tv
Read videos from a directory and reproduce them using a Raspberry Zero 2

## Instructions:

###  Encoding

To efficiently encode the videos for the Pi, follow these steps:

1. Early encoding: Start encoding the videos into the H264 format (480p) on your computer. This process might take some time, so beginning early is advisable.
2. Format and transfer: Place the encoded videos onto a thumb drive for easy transfer to the Pi later. Although other codecs might be smaller, H264 is recommended due to limited codec support on the Pi.
3. Avoid Pi Zero encoding: Do not encode videos directly on the Pi Zero as its processing power is minimal, and it will result in a significant wait time before being able to watch the videos.
4. Convenient encoding script: Utilize the provided script to automatically encode all videos in a designated folder to the proper format.
5. FFMPEG installation: If you don't have FFMPEG installed, follow the installation guides available on their GitHub page.
6. Organize files: Collect all videos in a folder and place the downloaded encoding script in the same folder for easy access.
7. Open the terminal, navigate to the folder (cd /path/to/the/folder), and run the script with: `sudo python encode.py`

### Autostart

To run the script each time the Pi boots, follow these steps:

1. Create a directory to store a script file (`mkdir /home/{user}/.config/autostart`)
2. Create a script file (`nano /home/{user}/.config/autostart/autostartvlc.sh`) and paste the following content:
```
export DISPLAY=:0
python /home/{user}/{location-of-your-player-script}/player.py
```
3. Grant the user privileges over that file `chmod u+x /home/{user}/.config/autostart/autostartvlc.sh`
4. Add the script to crontab by typing `crontab -e` and pasting the following content at the bottom:
```
@reboot /home/ctk59/.config/autostart/autovlc.sh &
```
